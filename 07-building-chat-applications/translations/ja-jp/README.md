# 生成 AI を利用したチャット・アプリケーションの構築

[![Building Generative AI-Powered Chat Applications](../..//images/07-lesson-banner.png?WT.mc_id=academic-105485-yoterada)](https://learn.microsoft.com/_themes/docs.theme/master/en-us/_themes/global/video-embed.html?id=57a31949-67c5-4020-8c85-91e4995589f3?WT.mc_id=academic-105485-yoterada)

> _(上記の画像をクリックすると、レッスン・ビデオを表示します)_

テキスト生成アプリの構築方法を見てきたところで、次にチャット・アプリケーションについて考えてみましょう。

チャットアプリケーションは私たちの日常生活に溶け込み、単なるカジュアルな会話の手段以上のものを提供しています。それらはカスタマー・サービスやテクニカル・サポート、さらには高度なアドバイザリー・システムの重要な部分を担っています。皆様も最近、チャットアプリケーションを通じて何らかの支援を受けた経験があるかもしれません。これらのプラットフォームに生成 AI などの先端技術を組み込むと、その複雑さは増し、それに伴い課題も増えてきます。

解答が必要な質問は下記の通りです。

- **アプリの構築** 特定のユースケースに対して、これらの AI を活用したアプリケーションを効率的に構築し、シームレスに統合するにはどうすればよいのでしょうか？
- **モニタリング** 一度デプロイした後、アプリケーションが機能面と[責任のある AI の六つの原則](https://www.microsoft.com/ai/responsible-ai?WT.mc_id=academic-105485-yoterada)の準拠という観点から、高品質で稼働している状態をどのようにして監視し、検証できるでしょうか？

自動化が進み、人間と機械が連続でやり取りする時代に突入する中で、生成 AI がチャット・アプリケーションの範囲、深さ、そして適応力をどう変化させるのかを理解するのが重要です。このレッスンでは、これらの複雑なシステムを支えるアーキテクチャを検討し、ドメイン（業種・業界）固有のタスクに合わせてそれらを微調整する方法を考えます。さらに、責任ある AI のデプロイを確実にするための指標と検討内容を学びます。

## はじめに

このレッスンでは、下記の内容について説明します。

- チャット・アプリケーションを効率よく実装し、統合するためのテクニック
- アプリケーションにカスタマイズと微調整を適用する方法
- チャット・アプリケーションを効果的に監視するための戦略と考慮点

## 学習目標

このレッスンを修了すると、下記を理解できます：

- チャット・アプリケーションを実装し、既存のシステムに統合する際の考慮点を説明する
- 特定のユースケースに合わせてチャット・アプリケーションをカスタマイズする
- AI を活用したチャット・アプリケーションの品質を効果的に監視し、維持するために重要な指標と考慮点を特定する
- 責任ある AI の原則をチャット・アプリケーションで適用する方法を確認する

## 生成 AI をチャット・アプリケーションに統合する

生成 AI を用いたチャット・アプリケーションは、ただ単にチャットアプリケーションをスマートにするだけではありません。アーキテクチャ、パフォーマンス、ユーザー・インターフェースを最適化し、質の高いユーザー・エクスペリエンスを提供できるようになります。これは、アーキテクチャの基盤、API 統合、ユーザー・インターフェースにおける検討事項の調査も含みます。このセクションでは、これらの複雑な領域を、既存のシステムに取り込むか、もしくはスタンドアロンのプラットフォームとして構築するかにかかわらず、効率的に進めるための包括的なロードマップを提供します。

このセクションを終了すると、チャットアプリケーションを効率的に実装し、統合するための専門知識を身につけられます。

### チャットボットとチャットアプリケーション、どちらが適している？

チャット・アプリケーションの実装に取り組む前に、「チャット・ボット」と「AI 搭載チャット・アプリケーション」を比較し、それぞれが果たす役割と機能の違いについて理解しましょう。チャット・ボットの主な目的は、FAQ への回答や荷物の追跡など、特定の会話タスクの自動化です。これは通常、ルール・ベースのロジックや複雑な AI アルゴリズムによって制御されます。それとは対照的に 「生成 AI を搭載したチャットアプリケーション」は、利用者との間でテキスト、音声、ビデオチャットなど、さまざまな形式のデジタル・コミュニケーションを可能にする、より広範囲な対話環境を提供します。その特徴は、微妙なニュアンスを持つ人間のような会話をシミュレートします。そして、さまざまな入力と文脈の手がかりを元に回答を生成する、生成 AI モデルを統合したアプリケーションです。生成 AI を搭載したチャット・アプリケーションは、特定のトピックや領域に限定せず、あらゆる種類のトピックや質問に対応します。そして会話が進むにつれて変化するトピックや状況変化にも対応でき、さらには創造的な対話や複雑な対話も生み出せます。

下記の表に、デジタルコミュニケーションにおける、各役割を把握する為の主な違いと共通点をまとめています。

| チャット・ボット               | 生成 AI を搭載したチャットアプリケーション                          |
| ------------------------------ | ------------------------------------------------------------------- |
| タスク中心でルールベース       | 文脈(コンテキスト)を理解する                                        |
| 大規模システムへの統合が多い   | 1 つまたは複数のチャット・ボットをホスト可能                        |
| プログラムされた機能に限定     | 生成 AI モデルを搭載                                                |
| 専門的で構造化された対話を行う | オープン・ドメインでの議論が可能 (特定のトピックや領域に限定しない) |

### SDK と API を活用した既存機能の利用

チャット・アプリケーションを開発する際、すでに利用可能なライブラリの有無と評価が大切です。チャットアプリケーションを SDK と API で構築すると、さまざまな利点があるため、有効な戦略と言えます。アプリケーションを戦略的に長期的な成功に導くためには、十分に文書化された SDK と API の使用が効果的で、スケーラビリティやメンテナンスの課題に対する対応も可能にします。

- **開発プロセスの迅速化とオーバーヘッドの削減**: 高コストの自作機能構築（車輪の再発明）ではなく、既存のライブラリを利用すると、ビジネスロジックなど、より重要と考えるアプリケーションやビジネス・ロジックの開発に集中できます。
- **パフォーマンスの向上**: 機能を一から構築する場合、最終的に「どのように拡張するのか？このアプリケーションは突然の利用者増加に対応できるのか？」と自分で考えなければなりません。適切にメンテナンスされた SDK と API を利用すると、こうした問題に対する解決策も提供してくれます。
- **メンテナンスの容易さ**: ほとんどの API と SDK で、新バージョンがリリースされた際、ライブラリを更新するだけで済むため、アップデートや改善が容易になります。
- **最先端技術へのアクセス**: 大規模なデータセットでファイン・チューニングやトレーニングされたモデルを活用すると、アプリケーションに自然言語処理の能力を追加できます。

SDK や API の機能を利用するためには、通常、提供されるサービスの使用許可を取得する必要があります。これは、一意のキーや認証トークンを使って行われます。OpenAI Python ライブラリを使って、これがどのように行われるのか確認してみましょう。また、このレッスン用の [OpenAI のノートブック](../../python/oai-assignment.ipynb?WT.mc_id=academic-105485-yoterada)や [Azure OpenAI Services のノートブック](../../python/aoai-assignment.ipynb?WT.mc_id=academic-105485-yoterada)を使って、自分で試せます。

```python
import os
from openai import OpenAI

API_KEY = os.getenv("OPENAI_API_KEY","")

client = OpenAI(
    api_key=API_KEY
    )

chat_completion = client.chat.completions.create(model="gpt-3.5-turbo", messages=[{"role": "user", "content": "生成 AI のチャット・アプリケーションに関するトレーニング・タイトルを2つ提案してください。"}])
```

上記の例では、GPT-3.5 Turbo モデルを使用してプロンプトを作成していますが、その前に API キーを設定している点にご注意ください。キーを設定しなかった場合は、下記のエラーが表示されます。

```output
AuthenticationError: No API key provided.
You can set your API key in code using 'openai.api_key = <API-KEY>',
or you can set the environment variable OPENAI_API_KEY=<API-KEY>).
If your API key is stored in a file, you can point the openai module
at it with 'openai.api_key_path = <PATH>'.
You can generate API keys in the OpenAI web interface.
See https://platform.openai.com/account/api-keys for details.
```

## ユーザーエクスペリエンス (UX)

一般的な UX の原則は、チャット・アプリケーション開発にも適用されますが、機械学習の要素が加わるため、追加で特に重要な検討事項がいくつかあります。

- **曖昧さへの対処方法**: 生成 AI モデルは、曖昧な回答を生成する場合があります。その際、詳細な情報を問い合わせできる機能を提供すると、利便性が高まります。
- **文脈（コンテキスト）の保持**: 高度な生成 AI モデルは、会話の文脈(会話履歴)を記憶する能力を持っており、ユーザー・エクスペリエンスにとって必要な要素になります。利用者に文脈を制御し管理する能力を与えると、ユーザー・エクスペリエンスは向上しますが、それと同時に、機密性の高い利用者情報を保持するリスクも生じます。この情報をどの位の期間保持するべきか、例えば保持期間のポリシーを導入するなどの検討が必要です。これにより文脈の必要性とプライバシーのバランスを保てます。
- **パーソナライゼーション**: 学習して適応する能力を備えた AI モデルは、利用者に対して個別にカスタマイズした利用者体験を提供できます。ユーザー・プロファイルを通じて利用者体験をカスタマイズできるようにすると、利用者は自分が AI に理解されていると感じると同時に、利用者に適した回答結果を得るのが容易になり、さらに効率的で満足度の高い対話が可能になります。

パーソナライゼーションの一例として、OpenAI の ChatGPT では「Custom Instructions（カスタム指示）」設定があります。これは、プロンプトに重要なコンテキストとなる自身の情報を提供できる機能です。下記に Custom Instructions（カスタム指示）の例を示します。

![Custom Instructions Settings in ChatGPT](../../images/custom-instructions.png?WT.mc_id=academic-105485-yoterada)

> [!TIP]
> 訳者追記  
> システムの問い> ChatGPT がより適切な回答を提供するために、あなたに関する情報を教えてください？
>
> 利用者の入力> 私は、大規模な上場ソフトウェア企業で上級職に就いています。2008 年からテクノロジーの専門家として活動しており、ソフトウェアエンジニアリングの修士号を持っており、熟練したプログラマーです。また、パートタイムでコンピュータサイエンスの教授も務めています。
>
> システムの問い> ChatGPT にどのように回答してほしいですか？
>
> 利用者の入力> ジャスミンと呼んでください。ChatGPT はいかなるトピックに対しても意見を述べます。

この「プロファイル」で、ChatGPT に Linked Lists（連結リスト）の学習計画を作成するように指示しています。ChatGPT は、利用者の過去の経験や経歴に基づいて、より詳細な学習計画が必要だと判断している点にご注意ください。

![A prompt in ChatGPT for a lesson plan about linked lists](../../images/lesson-plan-prompt.png?WT.mc_id=academic-105485-yoterada)

> [!TIP]
> 訳者追記  
> 利用者の入力> 連結リストの学習計画を作成してください
>
> 回答> もちろんです、ジャスミン！あなたのテクノロジーとコンピュータサイエンス教育のバックグラウンドを考慮すると、基本を超えた詳細な学習計画を望まれていると思います。下記に、コンピュータサイエンスにおける連結リストを教えるための学習計画を提案します。
>
> 学習計画：連結リストの理解と実装
>
> 所要時間  
> 1.5 時間
>
> 目標  
> このレッスンの終わりまでに、生徒は連結リストの概念を理解し、プログラミング言語でそれを実装し、連結リストを用いて問題を解決できるようになる。

### 大規模言語モデル用の Microsoft のシステム・メッセージ・フレームワーク

Microsoft は、大規模言語モデル（LLM）からの回答を生成する際に、効果的なシステムメッセージを作成するための[ガイダンス](https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message#define-the-models-output-format?WT.mc_id=academic-105485-yoterada)を提供しています。これは以下の 4 つの領域に分類できます：

1. モデルのプロファイル、機能、制限を定義する
2. モデルの出力形式を定義する
3. モデルの意図した動作を示す、具体例を提供する
4. 安全性と動作に関する追加のガードレールを定義する

### アクセシビリティについて

視覚や聴覚、運動能力、認知能力に関してご不自由のある方も、きちんと設計されたチャット・アプリケーションを利用できるように実装する必要があります。下記に、各利用者に対応するためにアクセシビリティを強化する機能をリストアップしました。

- 視覚にご不自由がある方向けの機能：ハイ・コントラストのテーマや、文字サイズの変更が可能なテキスト、スクリーンリーダーとの互換性
- 聴覚にご不自由がある方向けの機能：テキストから音声へ、音声からテキストへの変換機能、音声通知に対する視覚的な手助け
- 運動機能にご不自由がある方向けの機能：キーボードによるナビゲーションのサポート、音声コマンド
- 認知機能にご不自由がある方向けの機能：簡易化された言語オプション

## ドメイン固有言語モデルのカスタマイズとファイン・チューニング

会社の専門用語を理解し、お客様が一般的に抱く特定の質問に回答するチャット・アプリケーションを想像してみてください。そのためのアプローチとして、以下の二つが挙げられます。

- **DSL モデルの活用**：DSL はドメイン固有言語を意味します。ドメインの概念やシナリオを理解するために、特定のドメイン向けにトレーニングした DSL モデルを活用できます。
- **ファインチューニングの適用**：ファイン・チューニングとは、特定のデータを用いてモデルをさらに訓練するプロセスです。

## カスタマイズ ： DSL の使用

ドメイン固有言語モデル（DSL モデル）を活用し、専門用語で文脈に即した内容で AI と対話できれば、利用者の関心を高められます。DSL モデルは、特定の分野、業界、または主題に関連するテキストを理解したり生成するために、訓練またはファイン・チューニングされたモデルです。DSL モデルの利用方法には、ゼロから自分で訓練する方法から、SDK や API を通じて既存のモデルを利用する方法まで様々です。また、既存の事前に訓練済みモデルを取得して、それを特定のドメインに適応させるためにファイン・チューニングするのも選択肢の一つです。

## カスタマイズ：ファイン・チューニングの適用

ファイン・チューニングは、事前訓練済みのモデルが特殊なドメインや特定のタスクに対応できない場合に検討します。

例えば、医療に関する問い合わせは複雑で、多くの文脈が必要です。医療専門家が患者を診断する際には、ライフスタイルや過去の病歴など様々な要素に基づいて、さらに診断内容を裏付けるために最新の医学論文を調べる場合もあります。このような細かいニュアンスが求められるような場面においては、一般用の AI チャット・アプリケーションは信頼を得る情報源として期待できません。

### シナリオ: 医療アプリケーション

治療ガイドライン、薬物服用の影響、最新の研究結果などを素早く参照できるように、医療従事者を支援するチャット・アプリケーションを考えてみましょう。

通常のモデルは、基本的な医学の問い合わせに答えたり、一般的なアドバイスを提供するのには十分かもしれません。しかし、以下のような状況では対応が難しいかもしれません。

- **非常に特殊もしくは複雑なケース**：たとえば、ある神経科医が、「薬剤耐性を示す小児のてんかん治療における現在推奨されるプラクティスは何ですか？」とアプリケーションに尋ねる場合があります。
- **最新の情報が反映されていない**：一般的なモデルは、神経学や薬理学の最新の研究結果を取り入れた最新の回答を提供するのが、難しい場合もあります。

このような場合、専門的な医療データセットを用いてモデルをファイン・チューニングすると、こうした複雑な医療問題に対する回答内容の正確性と信頼性を著しく高められます。そのためには、取り組むべき専門分野の課題や疑問点を反映した、大規模で関連性の高いデータ・セットが必要です。

## 高品質な AI 駆動のチャット体験に必要な検討事項

このセクションでは、「高品質」なチャット・アプリケーションの基準を説明します。そのためには、実用的な指標(メトリクス)の取得方法や、責任ある AI の原則を取り入れたフレームワークの利用も含まれます。

### 重要な指標（メトリクス）

アプリケーションを高品質で高いパフォーマンスを維持するためには、重要な指標（メトリクス）と検討事項を把握する必要があります。これらの測定は、アプリケーションの機能性を保証するだけでなく、AI モデルとユーザー・エクスペリエンスの品質を評価するためにも必要です。下記に、基本的なメトリクス、AI に関するメトリクス、ユーザー・エクスペリエンスに関するメトリクスを検討するためのリストを示します。

| メトリック                          | 定義                                                                                                                                                                                                                                                                                                                                                                                                                            | チャット開発者の検討事項                                                                             |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| **アップタイム**                    | アプリケーションが稼働し、利用者が利用可能な時間を計測します                                                                                                                                                                                                                                                                                                                                                                    | ダウンタイムをどのようにして最小限に抑えられますか?                                                  |
| **応答時間**                        | アプリケーションが利用者からの問い合わせに応答するまでの時間                                                                                                                                                                                                                                                                                                                                                                    | クエリ処理をどのように最適化し、応答時間を改善できますか?                                            |
| **Precision（精度）**               | 真陽性予測の割合を、陽性予測の総数で割ったもの　</br></br>（訳者による追記：モデルで提供される正しい出力の数 (真陽性) と、陽性サンプルの総数 (真陽性+偽陽性) を比較 [ご参考：What Is a Confusion Matrix in Machine Learning?](https://plat.ai/blog/confusion-matrix-in-machine-learning/)）                                                                                                                                     | モデルの精度をどのように確認しますか?                                                                |
| **Recall （再現率） (Sensitivity)** | 真陽性予測の数を実際の真の数で割った比率 </br></br>（訳者による追記：真の値の総数に対する、正しく分類された陽性サンプル(TP)の数の比率として計算 [ご参考：What Is a Confusion Matrix in Machine Learning?](https://plat.ai/blog/confusion-matrix-in-machine-learning/)）                                                                                                                                                         | 　 Recall をどのように測定し、改善しますか?                                                          |
| **F1 スコア**                       | 精度と再現率の調和平均で、両者のバランスを示します </br></br>（訳者による追記：</br>F1 = 2*((Precision*Recall)/(Precision+Recall)) </br> F スコアまたは F メジャーは、テストの精度の尺度です。これは、テストの精度と再現率から計算され、精度は真陽性の結果の数を、正しく識別されなかったものを含むすべての陽性結果の数で割った値であり、再現率は、真陽性の結果の数を、陽性として識別されたすべてのサンプルの数で割った値です。) | 目指す F1 スコアは何ですか?精度と再現率のバランスをどのように調整しますか?                           |
| **Perplexity**                      | モデルが予測した確率分布が、データの実際の分布とどれだけ一致しているかを計測します。</br></br>(訳者追記：</br>[ご参考: Wikipedia パープレキシティ](https://ja.wikipedia.org/wiki/%E3%83%91%E3%83%BC%E3%83%97%E3%83%AC%E3%82%AD%E3%82%B7%E3%83%86%E3%82%A3))                                                                                                                                                                     | Perplexity をどのように最小限に抑えますか?                                                           |
| **利用者満足度指標**                | アプリケーションに対する利用者の評価を計測します。主にアンケートを通じて収集します                                                                                                                                                                                                                                                                                                                                              | ユーザーフィードバックはどのくらいの頻度で収集しますか?それに基づいてどのように改善策を立てますか?   |
| **エラー発生率**                    | モデルが理解や出力で間違いを犯す割合                                                                                                                                                                                                                                                                                                                                                                                            | エラー発生率を減らすための戦略は何ですか?                                                            |
| **再トレーニングサイクル**          | 新しいデータや知見を取り入れてモデルを更新する頻度                                                                                                                                                                                                                                                                                                                                                                              | どのくらいの頻度でモデルを再トレーニングしますか?再トレーニングサイクルを開始するトリガーは何ですか? |
| **異常検出**                        | 期待する動作に適合しない異常なパターンを識別するためのツールと手法                                                                                                                                                                                                                                                                                                                                                              | 異常が発生した際にどのように対応しますか?                                                            |

> [!TIP]
> 訳者追記：Precision（精度）、Recall （再現率）、F1 スコア、Perplexity は、機械学習の分野でよく使われるメトリクスです。これらのメトリクスの詳細については、[こちら](https://docs.microsoft.com/azure/machine-learning/how-to-understand-automated-ml#classification-metrics?WT.mc_id=academic-105485-yoterada)をご覧ください。
> モデルのファイン・チューニングや再トレーニングを行わない場合は、こちらのメトリクスは不要です。その場合は、利用者満足度指標やエラー発生率など、アプリケーションのパフォーマンスを測定するメトリクスを重視してください。

### チャット・アプリケーションにおける責任ある AI の実践導入

Microsoft の責任ある AI への取り組みでは、AI の開発と利用を導く 6 つの原則を定義しています。下記に、それらの原則、定義、及びチャット開発者が検討べき事項と、その重要性について説明します。

| 原則                       | Microsoft の定義                                                          | チャット開発者の検討事項                                                 | 重要な理由                                                                                   |
| -------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------- |
| 公平性                     | AI システムは全ての人を公平に扱うべきです                                 | 利用者データに基づく差別がないようにチャットアプリケーションを設計します | 利用者間で信頼と包括性を築き、法的な問題を避けるためです                                     |
| 信頼性と安全性             | AI システムは確実かつ安全に動作するべきです                               | エラーやリスクを最小限に抑えるためにテストとフェイルセーフを実装します   | 利用者の満足度を確保し、潜在的な危険を防ぐためです                                           |
| プライバシーとセキュリティ | AI システムは安全であり、プライバシーを尊重すべきです                     | 利用者データを保護するために強力な暗号化とデータ保護対策を実装します     | 利用者の機密データを保護し、プライバシー法に準拠するためです                                 |
| 包括性                     | AI システムは全ての人に力を与え、人々を惹きつけるものでなければなりません | 多様な利用者がアクセスしやすく使いやすい UI/UX を設計します              | 多くの人がアプリケーションを効果的に利用できるようにするためです                             |
| 透明性                     | AI システムは理解しやすいように実装すべきです                             | AI の回答について明確なドキュメントと理由を提供します                    | 利用者は、意思決定がどのように行われるかを理解できれば、システムを信頼する可能性が高まります |
| 説明責任                   | 人間は AI システムに対して説明責任を負うべきです                          | AI の意思決定をチェックし、改善するための明確なプロセスを確立する        | ミスが発生した際、継続的な改善と修正措置を可能にするためです                                 |

## 課題

[課題](../../python?WT.mc_id=academic-105485-yoterada)をご覧ください。最初のチャット・プロンプトの実行から、テキストの分類や要約など、一連の演習を行えます。

## お疲れ様でした!　学習を続ける

このレッスン修了後、[生成 AI 学習コレクション](https://aka.ms/genai-collection?WT.mc_id=academic-105485-yoterada) をチェックして、Generative AI の知識をレベルアップさせましょう。

レッスン 8 では、[検索アプリケーションの構築](../../../08-building-search-applications/translations/ja-jp/README.md?WT.mc_id=academic-105485-yoterada)方法を見ていきます。