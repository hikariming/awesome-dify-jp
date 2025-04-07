> オリジナルプロジェクト: [https://github.com/svcvit/Awesome-Dify-Workflow](https://github.com/svcvit/Awesome-Dify-Workflow)

> 注意：本プロジェクトはオリジナルの著作権を尊重し、一部のケースのみを提供しています。完全な内容が必要な場合は、オリジナルプロジェクトにアクセスし、Cursorを使用して翻訳してください。

# Awesome-Dify-Workflow

[English](README_EN.md) | [日本語](README.md)

実用的なDifyワークフローを共有します。個人使用や学習に適しています。Dify 0.10.0以上でインポートしてください。**並列タスク**、**セッション変数**、**フォーム**、**echartレンダリング**などの機能がサポートされています。

すべてのワークフローは基本的に**無料**で使用できます。より多くのワークフローを収集・整理中です...

## よくある質問
グループでよくある質問をまとめました。定期的に更新されます。簡潔な内容ですが、お役に立てれば幸いです。

<details>
<summary>サンドボックスでpandasなどのサードパーティライブラリをインストールするには？</summary>
答：/docker/volumes/sandbox/dependencies/python-requirements.txtを開き、必要な依存関係を追加して、sandboxを再起動します。
</details>

<details>
<summary>サンドボックスでnumpy>2.0、matplotlib、scikit-learnのコードを実行する際のエラーを修正するには？</summary>
答：<a href="https://github.com/svcvit/dify-sandbox-py">https://github.com/svcvit/dify-sandbox-py</a>を試してください。これは私が開発した簡略化されたサンドボックスで、権限制限を削除しています。
</details>

<details>
<summary>ノード間の文字列データ転送制限を処理するには？</summary>
答：.envで以下の行を修正します：
CODE_MAX_STRING_LENGTH: 1000000
TEMPLATE_TRANSFORM_MAX_LENGTH: 1000000
その後、コンテナを再起動します
</details>

<details>
<summary>チャットウィンドウで画像URLを使用して画像を表示できますか？markdownを試しましたが何も表示されません。</summary>
<img src="./images/image001.png" alt="サンプル画像" width="400">

答：あなたの方法は正しいですが、画像が表示されないのはクロスオリジンリクエストがサポートされていないためです
</details>

<details>
<summary>設定を修正しても、ナレッジベースへの大容量ファイルのアップロードが失敗します。以下がアップロードファイルの設定です：</summary>
<img src="./images/002.png" alt="サンプル画像" width="400">

答：Nginxの設定も修正する必要があります；.envファイルで'nginx'を検索してください
</details>

<details>
<summary>ナレッジベースの永久キューイング問題</summary>
答：.envでこの行を修正します：LOG_FILE=/app/logs/server.log；その後、コンテナを再起動します
</details>

<details>
<summary>DuckDuckGo翻訳は現在使用できませんか？</summary>
答：原因が分かりました - 私のサーバーにはプロキシがありますが、Dockerで実行されているDifyにはありません
</details>

<details>
<summary>Difyの公式サンプルアプリケーションを英語から日本語に変更するには？</summary>
答：右上のプロフィール画像をクリックし、設定、言語、まず他の言語に切り替えてから、日本語に切り替えます
</details>

<details>
<summary>管理者パスワードを忘れた場合はどうすればよいですか？</summary>
答：このコマンドを実行します：docker exec -it docker-api-1 flask reset-password
</details>

## モデル
OpenAIやAnthropicのモデルを体験したい場合は、[CoffBox](https://one.coffbox.com/)サービスを使用できます。設定手順は[How to Use CoffBox Service in Dify](https://blog.vcvit.me/2024/11/13/how-to-use-one-api-in-dify/)を参照してください。

## 参考スクリーンショット

すべてのDSLはワークフローモードで、ツールとして簡単に公開し、ChatBotプロセスに組み込むことができます。ワークフローには基本的な入力、条件判断、変数アグリゲーター、出力などのコンポーネントが含まれています。

# DSLディレクトリ

以下の各ymlの説明を参考にして必要なWorkflowを見つけ、DSLフォルダ内の対応するファイルを見つけ、ファイルのURLをコピーして、Difyアカウントにインポートできます。

## 2024-11-22更新

| ファイル | 説明 | ソース |
| ---- | ---- | ---- |
| `matplotlib.yml` | matplotlibを使用してプロットし、base64形式の画像を出力し、応答を通じてレンダリングします。注意：公式サンドボックスは権限が複雑で、インストール後もmatplotlibは使用できません。[dify-sandbox-py](https://github.com/svcvit/dify-sandbox-py)を使用してください ![](./snapshots/Xnip2024-11-21_09-35-09.jpg) | WeChat @svcvit |
| `jieba.yml` | Jieba分詞の例、[dify-sandbox-py](https://github.com/svcvit/dify-sandbox-py)を使用してください ![](./snapshots/Xnip2024-11-22_13-44-07.jpg) | WeChat @svcvit |

## 2024-11-20更新

| ファイル | 説明 | ソース |
| ---- | ---- | ---- |
| `json-repair.yml` | 大規模モデルの出力する非標準JSON（引用符の欠落、余分な括弧）を解析可能なJSONに修正します ![](./snapshots/Xnip2024-11-20_09-45-48.jpg) | WeChat @svcvit |

## 2024-11-15更新

| ファイル | 説明 | ソース |
| ---- | ---- | ---- |
| `json_translate.yml` | JSONの内容を解析して翻訳し、イテレーターを使用して翻訳し、新しいJSONに組み合わせて元の構造を維持します ![](./snapshots/Xnip2024-11-15_18-16-26.jpg) | WeChat @svcvit |

## 2024-11-14更新

| ファイル | 説明 | ソース |
| ---- | ---- | ---- |
| `腾讯云SubtitleInfo.yml` | 腾讯云の認証情報暗号化関連のコード例。コードノードの使用参考。 ![](./snapshots/Xnip2024-11-14_14-03-53.jpg) | WeChatグループ |
| `chart_demo.yml` | 応答内容を通じてチャートをレンダリングします。SQLクエリと組み合わせて必要な内容を生成することもできます ![](./snapshots/Xnip2024-11-14_15-17-39.jpg) | WeChat @svcvit |

## 2024-11-12更新

| ファイル | 説明 | ソース |
| ---- | ---- | ---- |
| `Form表单聊天Demo.yml` | ダイアログボックスでログイン後にモデルにアクセスします ![](./snapshots/Xnip2024-11-12_10-47-42.jpg) | WeChat @svcvit |

## 翻訳

| ファイル | 説明 | ソース |
| ---- | ---- | ---- |
| `中译英.yml` | 宝玉のPromptを使用し、直訳->反省->意訳で、中国語を高品質な英語に変換します。 ![](./snapshots/Xnip2024-07-24_13-04-11.jpg) | N/A |
| `DuckDuckGo 翻译+LLM 二次翻译.yml` | 3段階翻訳に似ていますが、最初の直訳を従来の翻訳エンジンに置き換え、tokensを節約し、品質を維持しながら翻訳効率を向上させます。 ![](./snapshots/Xnip2024-07-16_13-42-06.jpg) | N/A |
| `translation_workflow.yml` | アンドリュー・ングのAgentic Workflowを使用し、'入力言語'、'ターゲット言語'、'国'、'原文'を入力してより詳細な翻訳結果を得ます ![](./snapshots/Xnip2024-07-16_16-58-05.jpg) | [translation-agent](https://github.com/andrewyng/translation-agent) |
| `宝玉的英译中优化版.yml` | 宝玉の英訳中翻訳最適化版、主にpromptとXMLタグを最適化しています ![](./snapshots/Xnip2024-08-01_13-47-25.jpg) | [翻译 GPT 的提示词更新和优化](https://baoyu.io/blog/prompt-engineering/translator-gpt-prompt-v2-1-improvement) |
| `全书翻译.yml` | DIFY公式例、長文を分割し、イテレーターで翻訳し、新しいJSONに組み合わせます ![](./snapshots/Xnip2024-10-30_18-02-24.jpg) | DIFY公式探索 |

## ツール

| ファイル | 説明 | ソース |
| ---- | ---- | ---- |
| `SEO Slug Generator.yml` | ブログ記事のURL slugを生成します。宝玉のXを参考にしています ![](./snapshots/Xnip2024-07-24_13-06-35.jpg) | [twitter](https://x.com/dotey/status/1801280536125608265) |
| `Document_chat_template.yml` | ナレッジベースチャットテンプレート ![](./snapshots/Xnip2024-07-24_13-08-49.jpg) | [Winson-030](https://github.com/Winson-030/dify-DSL) |
| `搜索大师.yml` | SearXNGを使用して検索し、jinaを使用して検索内容を取得します ![](./snapshots/Xnip2024-07-24_13-07-55.jpg) | [Winson-030](https://github.com/Winson-030/dify-DSL) |
| `标题党创作.yml` | バズるウェブライター ![](./snapshots/Xnip2024-10-31_17-45-53.jpg) | [ghostviper](https://github.com/ghostviper/dify-workflow) |
| `文章仿写-单图_多图自动搭配.yml` | 記事の模倣 ![](./snapshots/Xnip2024-10-31_17-46-30.jpg) | [ghostviper](https://github.com/ghostviper/dify-workflow) |
| `Text to Card Iteration.yml` | 小红书カードを自動生成します。 | 🔥Dify Workflow-Agent設計交流グループ @Arthur |
| `Dify 运营一条龙.yml` | 小红书、抖音、微博、B站のワンストップ運営。（2024/11/21更新、画像生成サービスの問題と解像度制限により、画像生成が正しく行われません） ![](./snapshots/Xnip2024-07-24_16-34-29.jpg) | [Dify一键生成多尺寸封面和全平台文案](https://www.youtube.com/watch?v=kCrQp8YZTsQ) |
| `Jina Reader Jinja.yml` | TavilySearchとJinaに基づくQ&Aワークフロー ![](./snapshots/Xnip2024-07-29_14-43-54.jpg) | 🔥Dify Workflow-Agent設計交流グループ共有 |
| `llm2o1.cn.yml` | タスク分解->ステップ抽出->イテレーティブステップ実行->要約->結果出力 ![](./snapshots/Xnip2024-09-30_09-44-00.jpg) | [@okooo5km](https://x.com/okooo5km/status/1838801763778072862) |
| `dify_course_demo.yml` | 完全なコースを自動生成します。 ![](./snapshots/GZvTSh3aYAEMAQ5.jpeg) | [dify_course](https://github.com/pekingmuge/dify_course) |
| `simple-kimi.yml` | シンプルな自作Kimi ![](./snapshots/Xnip2024-10-31_17-33-34.jpg) | [aws-samples](https://github.com/aws-samples/dify-aws-tool/tree/main/workflow) |
| `Claude3 Code Translation.yml` | 異なるプログラミング言語間のコード翻訳ワークフロー ![](./snapshots/Xnip2024-10-31_17-38-34.jpg) | [aws-samples](https://github.com/aws-samples/dify-aws-tool/tree/main/workflow) |

## チャットボット

| ファイル | 説明 | ソース |
| ---- | ---- | ---- |
| `根据用户的意图进行回复.yml` | ユーザーの意図を判断し、異なるワークフローパスを選択し、それに応じて応答します ![](./snapshots/WechatIMG4894.jpg) | N/A |
| `mem0ai` | メモリ付きチャットボット ![](./snapshots/WechatIMG6110.jpg) | [dify-plugin-mem0ai](https://github.com/tonori/dify-plugin-mem0ai) |
| `记忆测试.yml` | 短期記憶を追加し、CoT思考チェーン例、自動Q&Aボットも自発的にトリガーでき、コンテキストに基づいて最適な応答を選択します ![](./snapshots/Xnip2024-09-19_12-03-01.jpg) | WeChat svcvit |

## コード

| ファイル | 説明 | ソース |
| ---- | ---- | ---- |
| `Python Coding Prompt.yml` | チャットダイアログを通じてPythonコードを生成します | [Sonnet 3.5 for Coding 😍 - System Prompt](https://www.reddit.com/r/ClaudeAI/comments/1dwra38/sonnet_35_for_coding_system_prompt/) |

## 使用方法

[Dify](https://cloud.dify.ai/)アカウントに登録し、モデルを追加します。

![snap](./snapshots/Xnip2024-07-16_13-17-53.jpg)

![snap](./snapshots/Xnip2024-07-16_13-17-10.jpg)

Workflow URLをコピーし、DSLファイルをインポートし、独自のWorkflowを公開して使用します。

![snap](./snapshots/Xnip2024-07-16_13-15-39.jpg)

![snap](./snapshots/Xnip2024-07-16_12-45-29.jpg)

![snap](./snapshots/Xnip2024-07-16_12-45-37.jpg)

