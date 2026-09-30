# 第1回 学習記録：AIエージェントとは何か

## 1. 今回の目的

- AIチャットとAIエージェントの違いを理解する。
- VS CodeとCodexを使って、AIエージェントが実際の開発環境で作業する流れを体験する。
- Gitの基本的な仕組みを実際に操作しながら理解する。
- AIに任せる作業と、人間が確認・判断する作業の違いを理解する。

## 2. 学んだこと

### 2.1 AIチャットとAIエージェントの違い

AIチャットは基本的に、

質問・依頼 → 回答

という形で利用する。

一方、AIエージェントは、より大きな目的や依頼に対して、

目的・依頼
  ↓
状況を確認
  ↓
実行方法を考える
  ↓
必要なツールを使う
  ↓
実際に作業する
  ↓
結果を確認する

という流れで、実際の環境に対して作業を行える。

今回の実習では、CodexがVS Code上のリポジトリを確認し、Gitコマンドを実行して状態を確認した。また、指定したファイルを実際に作成した。

重要なのは、単に「難しい質問に答えられるか」ではなく、AIが実際の環境に対してツールを使って操作できるかという点だと理解した。

### 2.2 CodexとVS Code

VS Codeは、コードやファイルを扱うための開発環境（IDE）として使用した。

今回の環境では、

- ファイルを見る
- ファイルを編集する
- ターミナルを使う
- Gitを操作する
- Codexを利用する

といった作業をVS Code上で行った。

Codexは、VS Code上で開発作業を支援するAIとして利用した。

ブラウザ上のChatGPTとVS Code上のCodexは、今回の学習において同じ会話内容をそのまま共有しているわけではない。

そのため、

- ChatGPT：学習、整理、設計、相談
- Codex：ローカル環境でのファイル操作、コマンド実行、コード作業

という役割分担を意識する必要がある。

### 2.3 Gitリポジトリ

Gitは、ファイルの変更履歴を管理する仕組みである。

今回、VS Codeで作成したフォルダをGitリポジトリとして設定するため、

git init

を実行した。

これによって、プロジェクトフォルダ内に.gitディレクトリが作成された。

また、GitとGitHubは別のものである。

- Git：ローカルで変更履歴を管理する仕組み
- GitHub：Gitリポジトリをインターネット上で管理・共有できるサービス

今回はGitHubにPrivateリポジトリを作成し、ローカルGitリポジトリと接続した。

### 2.4 untracked

untrackedは、Gitがまだ追跡していないファイルの状態。

Codexにagent-test.txtを新規作成してもらった直後、

?? agent-test.txt

と表示された。

これは、ファイル自体は存在しているが、まだGitの次のコミット対象として登録されていない状態だった。

### 2.5 staging area

Gitでは、ファイルの変更をいきなりcommitするのではなく、まず次のcommitに含める変更を選択できる。

そのための領域がstaging area（ステージングエリア）。

working tree
    ↓ git add
staging area
    ↓ git commit
commit（履歴）

という流れになる。

staging areaは、WindowsのExplorerやVS CodeのExplorerに表示されるようなフォルダではない。

Git内部で変更を管理するための領域であり、.git/indexが重要な役割を持つ。

git add agent-test.txtを実行すると、ファイルがstaging areaに登録された。

### 2.6 commit

commitは、staging areaに登録した変更をGitの履歴として保存する操作。

今回、

git commit -m "AIエージェントによるファイル作成を確認"

を実行し、最初のcommitを作成した。

commitによって、変更がGitの履歴として記録された。

### 2.7 branch

branchは、Explorer上のフォルダではなく、Gitの履歴上の作業位置を表す名前。

今回、git init直後のブランチはmasterだった。

その後、

git branch -M main

によってmainに変更した。

今回のGitHubリポジトリのmainブランチとの対応を分かりやすくするためであり、Gitを使ううえでmasterからmainへの変更が必須という意味ではない。

### 2.8 remote / origin

Gitでは、GitHubなどの外部にあるリポジトリをremote（リモート）として登録できる。

今回、

git remote add origin https://github.com/anakahama-dev/ai-agent-lab.git

として登録した。

ここで、originはリモートリポジトリそのものの名前ではなく、ローカルGitがそのリモートリポジトリを参照するためにつけた名前。

### 2.9 origin/main

origin/mainは、

origin
+
main

と考えると分かりやすい。

つまり、

originという名前で登録したremoteに対応するmainブランチ

を表している。

originはbranchではなくremoteの名前であり、mainがbranchの名前。

### 2.10 push

git pushは、ローカルGitリポジトリにあるcommitをremote側へ送る操作。

今回、

git push -u origin main

を実行し、ローカルのmainブランチのcommitをGitHubのorigin/main側へ送った。

これによってGitHub上でもagent-test.txtとcommit履歴を確認できた。

### 2.11 commitの対象

今回、learning/part01-ai-agent-and-git.mdをgit addし、agent-test.txtは変更したもののgit addしなかった。git diffにはstagingされていないagent-test.txtの変更が表示され、git diff --stagedにはstagingしたlearning/part01-ai-agent-and-git.mdの内容が表示された。この状態でgit commitすると、learning/part01-ai-agent-and-git.mdだけがcommit対象となり、agent-test.txtの変更は作業ツリーに残ることを確認した。
## 3. 実際に操作したこと

今回、以下を実際に操作・確認した。

### VS Code

- ai-agent-labフォルダをVS Codeで開いた。
- VS Codeのターミナルを使用した。
- CodexをVS Code上で起動した。

### Git

git --version
git init
git status
git add
git diff
git diff --staged
git commit
git branch -M main
git remote add origin
git remote -v
git push -u origin main

を実際に操作した。

### Codex

Codexに、

- リポジトリの状態確認
- ファイルの作成

を依頼した。

Codexが実際にGitコマンドやPowerShellコマンドを実行し、その結果を確認する様子を観察した。

### GitHub

- GitHubアカウントを作成した。
- Personal Accountを使用した。
- ai-agent-labというPrivateリポジトリを作成した。
- ローカルGitリポジトリとGitHubリポジトリを接続した。
- git pushでローカルのcommitをGitHubへ送った。
- GitHub上でファイルとcommitを確認した。

## 4. 自分の言葉で理解したこと

AIエージェントは、単に質問に答えるAIではなく、必要に応じて環境を調べたり、ツールを使ったりして、依頼された作業を実行できる。

今回、CodexがVS Code上のリポジトリを調べ、Gitの状態を確認したり、ファイルを作成したりしたことで、この違いを実際に確認できた。

また、Gitについては、

ファイル
 ↓
Gitが変更を認識
 ↓
git add
 ↓
staging area
 ↓
git commit
 ↓
Gitの履歴
 ↓
git push
 ↓
GitHub

という基本的な流れを実際に操作できた。

特に、untracked、staging area、commit、branch、remote、origin/mainは、それぞれ別の概念であることが分かった。
今回の実習で、commitの対象になるのはstaging areaに登録した変更だけであり、登録していないagent-test.txtの変更は作業ツリーに残ることを確認した。

今回の実習を通じて、更新するかどうか、何を更新するか、どこに更新するかなどは人間が判断することだと理解した。

また、「ファイルを更新したこと」「staging areaにaddしたこと」「commitしたこと」は、それぞれ別の操作・状態であることが分かった。

作業ツリーに未commitの変更を残したままにせず、現在どの変更が残っているのかを確認し、意図した状態にしておくことが重要だと感じた。

そして、CodexをはじめとしたAIエージェントが登場する以前は、このような確認や操作の多くを人間が手と目で行っていたのだと考えると、AIによって開発の進め方が大きく変わる可能性を感じた。

## 5. まだ曖昧なこと

- .gitの内部で、Gitが変更履歴やstaging areaをどのように管理しているのか。
- Gitのcommitやbranchが内部的にどのような構造になっているのか。
- Gitのコマンドをまだすべて覚えているわけではない。
- ChatGPTとCodexの間で、どのように情報を受け渡すのが適切なのか。
- Codexがどこまで自律的に判断してよいのか、どこから人間が明確に指示・確認すべきなのか。
- commitとpushのタイミングを間違えた場合に、ローカルとorigin/mainの状態がどのようにずれるのか、また、その状態をどのように確認・解消するのか。

## 6. 今回、人間が判断したこと

今回、人間が判断・確認したこととして、

- GitHubのアカウント名
- Gitのユーザー名
- Gitに登録するメールアドレス
- GitHubリポジトリをPrivateにすること
- ローカルリポジトリを作成する場所
- Codexにファイルを作成させること
- Gitへのstaging、commit、pushを実行すること
- AIが行った操作の結果を確認すること

などがあった。

特に、AIにファイル操作を任せる場合でも、何を変更してよいのか、何をしてはいけないのかを人間が判断することが重要だと分かった。

## 7. 今回、AIに任せたこと

Codexには、

- リポジトリの状態確認
- Gitの状態確認
- agent-test.txtの作成

を任せた。

その際、

- 既存ファイルを変更しない
- 既存ファイルを削除しない
- Gitのstagingやcommitを行わない

などの制約を指定した。

AIに作業を任せる場合、単に「作って」と依頼するだけではなく、対象、制約、完了条件を明確にすることが重要だと分かった。

## 8. 次回に向けて

今回、AIエージェント、VS Code、Codex、Git、GitHubなど、それぞれの役割や基本的な関係について学んだ。

実際に操作することで少しずつイメージできるようになってきた一方で、まだ全体としては「雲をつかむような」感覚も残っている。

特に、各ツールが内部でどのようにつながって動いているのか、AIエージェントがどこまで自律的に判断し、どこから人間が判断するべきなのかについては、今後の実習を通じて理解を深めたい。

次回以降も、単に説明を聞いて終わりにするのではなく、実際にVS CodeやCodexを操作し、自分で結果を確認しながら理解していく。

また、今回学んだGitについても、コマンドを暗記することより、

「今、自分はGitのどの状態にいるのか」

を意識して使えるようになることを目指す。
