# 第3回 解答

## 演習

- 第1回（素のLLM）とエージェントの回答の違い：
- `--trace` で見えたツール呼び出し（ツール名と引数）：
- 1つの質問での LLM 呼び出し回数（`requests`）：
- 追加したツールと、docstring に書いた説明：

## 宿題

- 取り組んだレベル：基礎
- やったこと：`app/agent.py` の `INSTRUCTIONS` から「用語や講座に固有のことを答える前に、必ず search_glossary で用語集を確認する」を削除し、同じ質問を `AIE_MODEL=gemini-3.1-flash-lite uv run python -m app.agent --trace "LoRAとQLoRAの違いは？"` で実行した。比較時のモデルをそろえるため、両方とも `gemini-3.1-flash-lite` を使用した。
- 結果：変更前は `search_glossary` を `LoRA` と `QLoRA` について各1回呼び、2回検索した。変更後は `LoRA` のみ1回検索した。どちらも `requests=2` だった。回答は両方とも2つの手法の違いを説明し、第2回に関連付けており、変更後はやや簡潔だった。
- 気づき・疑問：必須検索の指示を外しても、ツールの docstring や質問内容をもとに検索ツールが選ばれた。一方、検索する用語の数は変わったため、`INSTRUCTIONS` はツールを使うかだけでなく、呼び方にも影響しうる。
