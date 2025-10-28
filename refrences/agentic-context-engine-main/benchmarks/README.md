# ACE Benchmarks

Evaluation framework for Agentic Context Engineering (ACE) with multiple datasets and automatic metrics.

## Quick Start

```bash
# List available benchmarks
uv run python scripts/run_benchmark.py list

# Run ACE evaluation with train/test split (default)
uv run python scripts/run_benchmark.py finer_ord --limit 100

# Run baseline only (no ACE learning)
uv run python scripts/run_benchmark.py simple_qa --limit 50 --skip-adaptation

# Compare baseline vs ACE side-by-side
uv run python scripts/run_benchmark.py hellaswag --limit 50 --compare
```

## Available Benchmarks

| Benchmark | Description | Domain | Default Limit |
|-----------|-------------|---------|---------------|
| **finer_ord** | Financial Named Entity Recognition | Finance | 100 |
| **simple_qa** | Question Answering (SQuAD) | General | 200 |
| **simple_math** | Math Word Problems (GSM8K) | Mathematics | 100 |
| **mmlu** | Massive Multitask Language Understanding | General Knowledge | 500 |
| **hellaswag** | Commonsense Reasoning | Common Sense | 200 |
| **arc_easy** | AI2 Reasoning Challenge (Easy) | Reasoning | 200 |
| **arc_challenge** | AI2 Reasoning Challenge (Hard) | Reasoning | 200 |

## Command Options

```bash
uv run python scripts/run_benchmark.py <benchmark> [options]
```

**Key Options:**
- `--limit` - Override sample limit (always overrides config)
- `--model` - Model name (default: gpt-4o-mini)
- `--skip-adaptation` - Skip ACE learning (faster baseline)
- `--compare` - Run both baseline and ACE, then compare results
- `--epochs` - ACE adaptation epochs (default: 1)
- `--split-ratio` - Train/test split ratio (default: 0.8)
- `--online-mode` - Use continuous learning instead of offline
- `--prompt-version` - Use v1 or v2 prompts (default: v1)
- `--save-detailed` - Save per-sample results
- `--quiet` - Suppress progress output

## Examples

```bash
# Quick test with 10 samples
uv run python scripts/run_benchmark.py finer_ord --limit 10 --quiet

# Compare baseline vs ACE
uv run python scripts/run_benchmark.py simple_qa --limit 50 --compare

# Full ACE evaluation with v2 prompts
uv run python scripts/run_benchmark.py simple_qa --epochs 3 --prompt-version v2 --save-detailed

# Online learning mode
uv run python scripts/run_benchmark.py hellaswag --limit 100 --online-mode

# Custom train/test split (90/10)
uv run python scripts/run_benchmark.py mmlu --limit 100 --split-ratio 0.9

# Test all benchmarks quickly (baseline only)
for benchmark in finer_ord simple_qa hellaswag arc_easy; do
  uv run python scripts/run_benchmark.py $benchmark --limit 5 --skip-adaptation --quiet
done
```

## Output

Results saved to `benchmark_results/` with format:
- **Summary**: `{benchmark}_{model}_{timestamp}_summary.json`
- **Detailed**: `{benchmark}_{model}_{timestamp}_detailed.json` (if `--save-detailed`)

## Adding Custom Benchmarks

Create `benchmarks/tasks/my_benchmark.yaml`:

```yaml
task: my_benchmark
version: "1.0"

data:
  source: huggingface
  dataset_path: my/dataset
  split: test
  limit: 100

metrics:
  - name: exact_match
    weight: 1.0

metadata:
  description: "My custom benchmark"
  domain: "my_domain"
```

## Evaluation Modes

The benchmark script supports three evaluation modes:

1. **ACE Mode (default)**: Train/test split with learning
   ```bash
   uv run python scripts/run_benchmark.py simple_qa --limit 100
   ```

2. **Baseline Mode**: No learning, direct evaluation
   ```bash
   uv run python scripts/run_benchmark.py simple_qa --limit 100 --skip-adaptation
   ```

3. **Comparison Mode**: Runs both baseline and ACE, shows improvement
   ```bash
   uv run python scripts/run_benchmark.py simple_qa --limit 100 --compare
   ```

## Notes

- **Default 80/20 train/test split** prevents overfitting and shows true generalization
- The `--limit` parameter always overrides config file limits
- ACE adaptation improves performance through iterative learning
- Use `--compare` to see baseline vs ACE improvement side-by-side
- Overfitting warnings help identify when ACE memorizes vs generalizes
- Opik tracing warnings ("Failed to log adaptation metrics") are harmless