# 第6回 解答

## 演習

<!-- [tool call] の行は、表示された行をそのまま貼り付けてください。終わらなかった STEP は、空欄のままでかまいません。 -->

- STEP 1 のツールの名前：
- STEP 2 の [tool call]：
- STEP 3 の [tool call]：
- STEP 4 の [tool call]：
- 気づき・疑問：

## 宿題

<!-- 基礎・実装・発展のどれか1つに取り組めば完了です。 -->
## 宿題
- レベル:基礎
- やったこと:app/mcp_server.py に
  server.tool()(tools.get_lecture_summary) を1行追加した。
  エージェント側(mcp_servers.json、mcp_agent.py)は変更していない
  (git status で app/mcp_server.py のみの変更を確認)。
- 結果:
  - --list-tools で、ツールが1個から2個に増え、
    glossary_get_lecture_summary が表示された
  - 「第2回では何を学びますか?」で
    [tool call] glossary_get_lecture_summary({'lecture': 2}) が呼ばれた
  - 「LoRAとは何ですか?」では
    [tool call] glossary_search_glossary({'query': 'LoRA'}) が呼ばれた
  - uv run pytest -q は 21 passed
- 気づき・疑問:
  - エージェント側を変えずに、サーバー側に1行足しただけでツールが1個から2個に増えた。エージェントが起動のたびにサーバーへ一覧を問い合わせているためだと分かった。
  - 「第2回では何を学びますか?」では get_lecture_summary、「LoRAとは何ですか?」では search_glossary が選ばれた。質問の種類によって使い分けられていた。
  - 疑問:「LoRAとは何ですか?」の回答の末尾に「第2回</code>」という文字が混ざっていた。原因がツールの返すデータかモデルの出力かは未確認。
