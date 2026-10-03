# 学習進捗

## 学習状況

- 第1回「AIエージェントとは何か」：完了
- 次の学習対象：第2回「VS Code・Codex環境」

## 第1回：AIエージェントとは何か

### 実際に操作して確認したこと

- VS CodeでローカルGitリポジトリを開いた。
- CodexをVS Codeで利用した。
- Codexにローカルリポジトリの状態を確認させた。
- Codexにファイルを新規作成させた。
- `git status`でuntrackedを確認した。
- `git add`でstaging areaへの追加を確認した。
- `git diff`と`git diff --staged`の違いを実際に確認した。
- `git commit`を実行した。
- GitHubのリモートリポジトリを設定した。
- `git push`でGitHubへ同期した。
- `git restore`で未commitの変更を元に戻した。
- 最終的にworking tree cleanを確認した。
- 学習記録 `learning/part01-ai-agent-and-git.md` を作成し、commit・pushした。

### 理解できたこと

- AIチャットとAIエージェントの違い。
- AIエージェントは目的に対して状況確認・判断・ツール実行を行えること。
- CodexはVS Code上でローカルのファイルやGitなどを扱えること。
- working tree、staging area、commit、remoteの基本的な関係。
- untracked、staging、commit、pushがそれぞれ別の状態・操作であること。
- `git diff`は主にworking treeとstaging areaの差を確認すること。
- `git diff --staged`はstaging areaとcommitの差を確認すること。
- AIに作業を任せても、何を変更するか・どこを変更するか・変更をcommit/pushするかなどは人間が判断する必要があること。
- ChatGPTとVS Code上のCodexは自動的に同じ会話内容を共有するわけではなく、ファイルやMarkdownなどを橋渡しとして利用すること。

### まだ曖昧なこと

- HEAD、branch、origin/mainなどが内部でどのようにつながっているのか。
- Gitがworking tree、staging area、local repository、remote repositoryをどのように管理しているのか。
- commitとpushのタイミングを間違えた場合に、ローカルとorigin/mainがどのようにずれるのか、またどう解消するのか。
- Gitのコマンドを暗記することではなく、Gitの状態を構造として理解すること。

### 学習上の振り返り

- 第1回を通じて、AIエージェントが実際の開発環境でファイル操作やGit操作を行えることを体験した。
- AIが作業を実行できる一方で、人間が変更内容や実行範囲、commit・pushなどの判断を行うことが重要だと理解した。
- Gitについては操作方法を実際に確認できたが、内部の仕組みについてはまだ「雲をつかむような」感覚がある。
- 今後はコマンドの暗記よりも、Gitの状態と各操作の関係を理解することを重視する。

## 第2回：VS CodeとCodexの連携

### 学習目的

VS CodeのWorkspaceと、Codexが作業対象のファイルを参照する仕組みを理解する。

### 実施したこと

- VS Codeで `ai-agent-lab` を開いた状態で、CodexにWorkspace内のファイルの参照を依頼した。
- `agent-test.txt` と `PROGRESS.md` の本文を確認するよう依頼した。
- `agent-test.txt` の文章をエディタ上で選択し、その文章を根拠として説明するよう依頼した。
- ファイルの編集・作成・削除、ターミナルコマンドの実行、Git操作を禁止して確認を行った。

### 確認できたこと

- VS Codeでファイルを開くことと、Codexがそのファイルの本文を直接参照できることは、同じではない。
- `agent-test.txt` では、選択した文章がCodexに渡され、その文章を引用した説明が返された。
- 今回の試行では、`agent-test.txt` と `PROGRESS.md` の本文をCodexが直接参照できたことは確認できなかった。

### まだ理解を深めること

- VS CodeのWorkspaceとCodexの参照対象の関係
- エディタで選択した文章がCodexに渡る仕組み
- ファイルの参照と、ファイルの編集・コマンド実行の違い
- Codexが実際に参照した情報と、推測した情報を区別する方法

### 振り返り

AIの回答だけで、ファイルを実際に参照できたと判断してはいけない。参照元と回答内容を照合し、確認できた事実と推測を区別する必要がある。
