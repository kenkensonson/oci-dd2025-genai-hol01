# Oracle Developer Day 2025

Oracle Developer Day 2025の[ハンズオンセッション](https://www.oracle.com/jp/developer/events/dev-day/#tab2)にご参加いただける方向けの記事です。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/301c3fe3-d8b6-4e9c-b693-38b1cca6fac8.png)

お申込みいただいた方には事前にOracle Cloudでのアカウント登録方法についてのメールが送信されています。本手順書は事前にアカウントが登録されていることが前提になっています。

# 本ハンズオンの内容
OCI Generative AI ServiceをプレイグラウンドとPython環境から操作するハンズオンです。

**ハンズオンの時間**
約40分

**ハンズオンの内容**
下記2項目
1. Generative AI Serviceをプレイグラウンドで体験
    - テキスト生成モデル
    - マルチモーダルモデル
    - 埋め込みモデル
2. Generative AI ServiceのPythonでの操作を体験
    - 事前準備
    - テキスト生成モデル
    - マルチモーダルモデル 

# ログイン後、リージョン確認

作成したアカウントでオラクルクラウドにログインすると下記のトップページが表示されます。

まず、右上赤枠のリージョンがGenerative AI Serviceを利用できるリージョンであることを確認してください。(今回は Chicagoリージョンになっているはずです。)

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/382d49c4-55fa-4702-884f-24638852545a.png)

左上赤枠がコンソールメニューバーとなり、ここから様々なサービスや設定画面に移動できます。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/90efed45-0866-48d3-a23d-f6943f5e31cd.png)


# OCI Generative AI Serviceのプレイグラウンド

まず初めに、OCI Generative AI Serviceのプレイグラウンドで基本機能を確認します。
下記のようにメニューを辿って、OCI Generative AI Serviceのプレイグラウンドのページに移動してください。

**コンソールメニュー　＞　アナリティクスとAI　＞　生成AI**

プレイグラウンドの画面
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/b95da326-de86-4316-beae-ac3952087650.png)

モデル詳細の表示ボタンをクリックし、選択できるモデルを確認します。

選択できるモデル
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/3d0aedba-4e0f-42cb-8fb0-7e90f131a63b.png)

### チャットモデルを試す

モデルを選択し、テキストフィールドに質問を入力、送信ボタンをクリックします。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/a4bc7296-12cf-4326-b987-5df00ef21e50.png)

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/8b0b8166-24be-4c2e-9bed-126c0618e2c5.png)

質問に対するテキストが生成されていることがわかります。

①まずはいくつかの質問を投げかけてみてください。
②チャット画面右の入力でLLMのパラメータを変更することができますので変更しながら同じように質問を投げかけてみてください。
結果の変化が分かりやすいパラメータとしては下記です。
- 最大出力トークン：生成する文字数の最大数です。
- プリアンプル・オーバーライド：会話スタイルを変更できるガイドライン・メッセージ(システム・メッセージ)です。(入力例としては「友達口調で応答してください。」などです。
- 温度：生成されるテキストのランダム性です。0から指定でき1に近いほど応答テキストのランダム性が増します。

### マルチモーダルモデルを試す

次にマルチモーダルのテキスト生成モデル Llama 3.2 Visionのモデルを試します。
下記画像をdog.jpegという名前でローカルに保存してください。

![dog.jpg](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/b1df0b55-182b-4d0a-8c78-f04f0243649e.jpeg)

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/1c50c0f6-e8cb-467a-9fdd-40aec0af0bcb.png)

保存した画像をテキストフィールド上部にドロップし、質問を入力し、送信ボタンをクリックします。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/10278a80-8341-467e-92bf-6a91ebaeda1c.png)

画像ファイルの説明テキストが生成できていることがわかります。

### 埋め込みモデルを試す

次に埋め込みモデルを試します。埋め込みモデルとは入力されたテキストの意味や文脈をベクトルデータに変換するモデルです。モデルとしては cohere.embed-multilingual-v3を使用します。


![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/273551d8-b20f-4c1e-8f0a-68542bc5172f.png)

サンプルの文章として下記4つを入力し、実行ボタンをクリックします。

1. 私は今日学校に行って数学を勉強しました。
2. 私は今日学校に行って算数を勉強しました。
3. 私は今日病院に行って健康検査をしました。
4. 私は今日会社に行って仕事をしました。

実際には1024次元のベクトルに変換されていますが、下記表示ではそれを2次元に圧縮し、表示しています。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/2681764f-be95-4601-b063-0c819ec23dd9.png)

文章からもわかる通り、1と2は文章の意味合いが非常に近いですが、3と4は遠くなっており人間の感覚と一致していることがわかります。

「埋め込みをJSONにエクスポート」ボタンをクリックするとベクトル値の入ったファイルをダウンロードできます。ファイルを開くと下記のように1024次元のベクトルに変換されていることがわかります。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/dacd6c51-6f94-4744-929c-479347303c31.png)

実際に生成AIのアプリケーションを開発する場合はGenerative AI ServiceにAPIでアクセスすることになります。その際のサンプルコードを確認します。

チャット画面に戻り、チャットモデルを選択し、サンプルコードの確認ボタンをクリックします。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/44f443c7-0816-4a79-b00b-8beb94059a4d.png)

下記のようにJavaとPythonのサンプルコードを確認することができます。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/46de99c3-30b9-4c3d-a8bc-b48b5c2b45b2.png)

以降はこのサンプルコードを実行するための設定手順と実際にサンプルコードを実行する手順になります。

# ハンズオンの構成
ハンズオンの構成は下図の通りです。既に作成済のテナントに新にコンパートメントを作成し、Pythonの実行環境としてOCI Data Science Serviceのインスタンスをセットアップします。そこからOCI Generative AI ServiceにPythonプログラムでアクセスするという流れです。このアクセスはAPIキーで保護されています。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/dbafdaed-3531-48a3-914c-b392144c134e.png)

これに合わせて、以降は下記6つの手順を実施します。

1. コンパートメントの作成
2. OCI Data Science Serviceのインスタンス作成
3. Conda仮想環境の作成
4. APIキーのセットアップ(OCICLIの)
5. ノートブックの作成
6. サンプルコードの実行


# コンパートメントの作成

コンパートメントを作成します。下記のように辿ってコンパートメント作成画面に移動してください。

**コンソールメニュー　＞　アイデンティティとセキュリティ　＞　コンパートメント　＞　コンパートメントの作成ボタン**

設定項目としては下記の通りです。
- 名前：hol（任意）
- 説明：hol（任意）

その他の項目はデフォルトでコンパートメントの作成ボタンをクリックしてください。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/68fb3ec2-09b7-43a7-b24b-f59285477583.png)



# OCI Data Science Service　のインスタンス作成

作成したコンパートメントにOCI Data Science Service のインスタンスを作成します。
下記のように辿って、プロジェクトを作成画面に移動します。

**コンソールメニュー　＞　アナリティクスとAI　＞　データサイエンス　＞　プロジェクトの作成**

作成済みのコンパートメントであることを確認しプロジェクトの作成ボタンをクリックします。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/5f9f4b6c-fe55-4233-97bc-f6042422258b.png)

設定項目は下記の通り。
- コンパートメント：hol
- 名前：hol（任意）

作成ボタンをクリックしプロジェクトを作成します。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/7422b25c-ecb5-462e-adf6-cdc4d8a0b78f.png)


作成済のプロジェクトにノートブックセッションを作成します。
ノートブックセッションの作成ボタンをクリックします。


![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/a70de870-e34d-4145-8c5f-5e79b2ddf2df.png)

ノートブック・セッションの作成画面での設定項目は下記の通り。
- コンパートメント：hol
- 名前：hol（任意）

更に、シェイプの変更ボタンをクリックし、シェイプを設定します。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/0d5ecbbc-63a4-465f-a7af-991a14d37d8d.png)



今回はVM.Standard.E4.Flexインスタンスを使用します。
下記のリソースを選択します。

- インスタンス・タイプ：仮想マシン
- シェイプシリーズ：AMD

次に、シェイプの選択ボタンをクリックします。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/a0a97754-2d9a-40b1-b409-286535693e2d.png)

ここでCPU、メモリのリソース設定を行います。
今回は下記のリソースで十分です。

- OCPU : 2
- メモリー : 16

その他の項目についてはデフォルトで問題ありません。作成ボタンをクリックします。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/22c15058-706f-4066-97ce-faeb2c9ec3d2.png)

ノートブック・セッション作成画面に戻り、作成ボタンをクリックします。
(今回ブロックストレージのサイズはデフォルトの100GBで十分なので指定しません。)

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/90c4aaa3-184b-40ca-bacd-31bb9c992ed4.png)

作成したノートブック・セッションは数分で起動します。作成したノートブックのリンクをクリックし詳細画面に移動します。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/3d52ffef-78ac-467b-be40-7dc77251fe86.png)

ノートブックセッションの「開く」ボタンをクリックしノートブックの画面に移動します。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/5d65b101-55d6-4301-9060-4d516680ab1e.png)

下記の画面が表示されればノートブックが利用可能な状態になっています。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/aaf79cf6-7c78-4999-b8f7-fcdc10434f99.png)

# Conda仮想環境の作成

作成したノートブックセッションのPython環境にConda仮想環境を作ってゆきます。
まずはTerminalのアイコンをクリックし、ターミナルを開きます。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/9eea1d8f-80a9-440e-8bea-a62d362e4547.png)

ターミナルで下記コマンドを実行し、Conda仮想環境を作成します。

```bash
odsc conda install -s python_p312_any_x86_64_v1 
```

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/38dd5def-b065-458d-9bfb-842a6de110cd.png)

コマンドの実行はconda仮想環境が作成されている状態です。

# APIキーの登録
APIキーの登録に必要なRSAキー・ペアと認証設定ファイルをOCICLIで作成します。

まず、OCICLIセットアップ時に入力が求められるユーザーOCIDとテナンシOCIDをメモ帳などにコピーしておく作業を行います。

コンソール右上のプロファイルメニューからユーザー名をクリックし、ユーザーの詳細画面に移動します。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/b0e2fb2c-4cfb-46a9-9423-12fab2e5a8c0.png)

ユーザーの詳細画面にてOCIDの項目の右側のコピーボタンをクリックし、メモ帳などにペーストします。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/1021df15-a4cd-44ec-83cd-bf83622fe166.png)

値としては以下のようなものになっているはずです。こちらがユーザーOCIDです。

```text
ocid1.user.oc1..aaaaaaa<中略>nqjja
```

同じくコンソール右上のプロファイルメニューからテナンシをクリックし、テナンシの詳細画面に移動します。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/0b960443-729e-40b7-b19b-f0c458817203.png)

同じく、テナンシの詳細画面にてOCIDの右側にあるコピーボタンをクリックし、メモ帳などにペーストします。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/b4ea20d1-9cce-4f00-b09c-ef7ccde42aec.png)

値としては以下のようなものになっているはずです。こちらがテナンシOCIDです。

```text
ocid1.tenancy.oc1..aaaaaaaas<中略>vcmp4qsq

```

次にOCICLIのセットアップです。ターミナルから下記コマンドを実行します。

```bash
oci setup config 
```

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/41846de2-5232-4633-9808-7729bf2dd328.png)

コマンドプロンプトで求められる以下の項目を入力します

```bash
# 入力なしでリターン。
Enter a location for your config [/home/datascience/.oci/config]: 

# ご自身のユーザーOCIDを入力しリターン。
Enter a user OCID : ocid1.user.oc1..aaaaaxxxxxxxxxxxx

# ご自身のテナンシOCIDを入力しリターン。
Enter a tenancy OCID:　ocid1.tenancy.oc1..aaaaaaaxxxxxxxxxx

# ご自身の利用リージョンを入力しリターン。(今回はus-chicago-1です。)
Enter a region by index or name : us-chicago-1

# RSAキーペアを作成します。「Y」でリターン。
Do you want to generate a new API Signing RSA key pair? (If you decline you will be asked to supply the path to an existing key.) [Y/n]: Y

# 入力なしでリターン。
Enter a directory for your keys to be created [/home/datascience/.oci]:

# 入力なしでリターン。
Enter a name for your key [oci_api_key]:

# パスワードは任意ですが、今回は Welcome1#Welcome1# で設定してください。
Enter a passphrase for your private key ("N/A" for no passphrase): Welcome1#Welcome1#
Repeat for confirmation:
Do you want to write your passphrase to the config file? (If not, you will need to enter it when prompted each time you run an oci command) [y/N]: y
```

上記の入力でRSAキーや認証設定ファイルが ~/.oci ディレクトリに作成されている状態になります。
作成された公開鍵をAPIキーとして登録しますので下記コマンドで鍵を表示してターミナルでコピーしてください。

```bash
(base) bash-4.4$ cat ~/.oci/oci_api_key_public.pem 
-----BEGIN PUBLIC KEY-----
MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAze4tiewg+rHcTJE/dDdO
(マスク)
Kr8pHLBX391XRRCJfm6KyzifZCF5SzJWGzQ06Zk/2c+Z33bWzKy7/CU+3mK1+bQ6
tQIDAQAB
-----END PUBLIC KEY-----
```

次にコンソール右上のプロファイルからユーザー名をクリックし、ユーザーの詳細画面に移動します。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/f4b0d5ef-4423-4b62-b140-4f5b4f41260f.png)


ユーザー詳細画面左のトークンおよびキーをクリックし、APIキーの追加ボタンをクリックします。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/54de0f6c-c2db-46d1-9c2b-f26d494374d4.png)

公開キーの貼り付けを選択し、先ほどコピーした公開鍵を公開キーのフィールドにペーストし、追加ボタンをクリックします。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/e0b14a2b-bc3f-4a57-a50a-125b845eae2f.png)


下記確認画面で閉じるボタンをクリック。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/e8b2a0ef-e361-49c6-92d8-884ffa8dc57f.png)

APIキーが追加されていることが確認できます。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/e3b075c3-2f9a-47b5-8d21-564dcca6fbad.png)

認証ができるかどうかを確認します。
Data Science Serviceの画面に戻り、terminalから下記コマンド(利用できるリージョンのリストを表示)を実行し、結果が表示されることを確認してください。

```bash
(base) bash-4.4$ oci iam region list
{
  "data": [
    {
      "key": "ORD",
      "name": "us-chicago-1"
    },
...
...

```

環境構築は以上で完了です。





# ノートブックの作成

Data Science Serviceの画面から、左ペインで右クリックし、New Notebookをクリックします。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/cd018141-3054-4848-b6b8-d9e82c93ee23.png)

作成済みのカーネルを選択します。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/545442d0-5853-4f34-be6a-6ec9ae8023ba.png)


念のためノートブック右上のカーネル名を確認し、作成済のConda仮想環境であることを確認してください。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/ac3f6d8f-c376-4c86-8bab-d3ec07ab0bed.png)

ここまでの設定により、Data Science ServiceからPythonコードを実行すると、APIキーの認証により、Generative AI ServiceにAPIアクセスできるようになりました。

# サンプルコードの実行

コンソールメニューから下記の通り辿り、生成AIサービス(Generative AI Service)の画面に移動します。

**コンソールメニュー　＞　アナリティクスとAI　＞　生成AI**

左ペインでチャットを選択、次にモデル(cohere.command-r-plus-08-2024)を選択し、コードの表示ボタンをクリックします。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/276d1b49-2b82-4ed9-88c3-b5fb30caaa6b.png)

下記がサンプルコードになります。これをコピーし、Data Science Serviceのノートブックにペーストします。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/c0920020-3d03-4f83-acce-4f20b5d5db1e.png)

下記が実行コードです。
ペーストしたコードからの変更点は下記の通りです。
- chat_request.messageに質問したい文章を記載

```python
import oci

# APIキーによる認証情報の定義
compartment_id = "<ご自身のコンパートメントID>"
CONFIG_PROFILE = "DEFAULT"
config = oci.config.from_file('~/.oci/config', CONFIG_PROFILE)

# Generative AI ServiceのService endpoint
endpoint = "https://inference.generativeai.us-chicago-1.oci.oraclecloud.com"

# クライアントの定義(Generative AI Service側がサーバーとなり、そのサーバーに接続するクライアントを定義します)
generative_ai_inference_client = oci.generative_ai_inference.GenerativeAiInferenceClient(config=config, service_endpoint=endpoint, retry_strategy=oci.retry.NoneRetryStrategy(), timeout=(10,240))

# チャットリクエストの詳細情報を格納するためのオブジェクトを作成
chat_detail = oci.generative_ai_inference.models.ChatDetails()

# Cohereモデルへのチャットリクエスト用のオブジェクトを作成
chat_request = oci.generative_ai_inference.models.CohereChatRequest()

# ユーザーからのメッセージを設定（質問内容）
chat_request.message = "日本の首相は誰ですか？"

# LLMのパラメータ値の定義
chat_request.max_tokens = 600　# 最大トークン数（生成するテキストの長さの上限）を設定
chat_request.temperature = 1　# creativity（創造性）の度合いを設定（1だと高めのランダム性）
chat_request.frequency_penalty = 0　# 頻度ペナルティ（同じ語の繰り返し抑制度合い）を設定（0で無効）
chat_request.top_p = 0.75　# nucleus sampling（確率分布の上位p%のみを候補とする）の閾値を設定
chat_request.top_k = 0　# top-k sampling（確率が高いk個のトークンから選ぶ）のk値を設定（0で無効化）

# 使用するモデルを設定（オンデマンドモードでモデルIDを指定）
chat_detail.serving_mode = oci.generative_ai_inference.models.OnDemandServingMode(model_id="ocid1.generativeaimodel.oc1.us-chicago-1.amaaaaaask7dceyapnibwg42qjhwaxrlqfpreueirtwghiwvv2whsnwmnlva")

# 作成したチャットリクエストを chat_detail にセット
chat_detail.chat_request = chat_request

# 使用する OCI コンパートメントの OCID を指定
chat_detail.compartment_id = compartment_id

# Generative AI サービスにチャットリクエストを送信し、応答を受け取る
chat_response = generative_ai_inference_client.chat(chat_detail)

# 結果を出力（チャット応答の内容を表示）
print("**************************Chat Result**************************")
print(vars(chat_response))
```

実行すると下記のような出力となります。
textの項目で応答テキストが出力されていることがわかります。

```python
**************************Chat Result**************************
{'status': 200, 'headers': {'content-type': 'application/json', 'opc-request-id': '2D8FE0FB24D947BB901A9B6CA9D7E68A/C63F826A42E48F10255E6C49149B4549/69A08F8A02DF11AA91CCDE758DD34FA1', 'content-encoding': 'gzip', 'content-length': '473'}, 'data': {
  "chat_response": {
    "api_format": "COHERE",
    "chat_history": [
      {
        "message": "日本の首相は誰ですか？",
        "role": "USER"
      },
      {
        "message": "2023年10月現在、日本の首相は**岸田文雄**（きしだ ふみお）です。彼は2021年10月に第100代内閣総理大臣に就任しました。",
        "role": "CHATBOT",
        "tool_calls": null
      }
    ],
    "citations": null,
    "documents": null,
    "error_message": null,
    "finish_reason": "COMPLETE",
    "is_search_required": null,
    "prompt": null,
    "search_queries": null,
    "text": "2023年10月現在、日本の首相は**岸田文雄**（きしだ ふみお）です。彼は2021年10月に第100代内閣総理大臣に就任しました。",
    "tool_calls": null,
    "usage": {
      "completion_tokens": 50,
      "completion_tokens_details": null,
      "prompt_tokens": 7,
      "prompt_tokens_details": null,
      "total_tokens": 57
    }
  },
  "model_id": "ocid1.generativeaimodel.oc1.us-chicago-1.amaaaaaask7dceyapnibwg42qjhwaxrlqfpreueirtwghiwvv2whsnwmnlva",
  "model_version": "1.0"
}, 'request': <oci.request.Request object at 0x7f0349c35d00>, 'next_page': None, 'request_id': '2D8FE0FB24D947BB901A9B6CA9D7E68A/C63F826A42E48F10255E6C49149B4549/69A08F8A02DF11AA91CCDE758DD34FA1'}

```

マルチモーダルモデルのLlama 3.2 Visionも実行してみます。
ローカルにダウンロードしたdog.jpegファイルをData Science Serviceにアップロードします。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/109260/9258058e-6c43-4ac2-b441-b6b889931f42.png)

下記のコードをノートブックで実行します。こちらはGenerative AI Serviceのコンソールで確認されるコードではなく下記のコードを実行してください。

ペーストしたコードからの変更点は下記の通りです。
- compartment_idにはご自身のものを定義(一つ前のコードのcompartment_idをコピー＆ペーストしてください。)
- image_pathに画像ファイルdog.jpegを定義
- content_text.textに入力プロンプトをていｇ

```python
# coding: utf-8
import oci
import base64

# ユーザー設定
compartment_id = "<ご自身のコンパートメントID>"
CONFIG_PROFILE = "DEFAULT"
image_path = "dog.jpeg"

# OCI config 読み込み
config = oci.config.from_file('~/.oci/config', CONFIG_PROFILE)

# Generative AI サービスのエンドポイント
endpoint = "https://inference.generativeai.us-chicago-1.oci.oraclecloud.com"

# クライアント作成
generative_ai_inference_client = oci.generative_ai_inference.GenerativeAiInferenceClient(
    config=config,
    service_endpoint=endpoint,
    retry_strategy=oci.retry.NoneRetryStrategy(),
    timeout=(10, 240)
)

# 画像をbase64にエンコード
with open(image_path, "rb") as image_file:
    encoded_image = base64.b64encode(image_file.read()).decode("utf-8")

# テキストコンテンツの作成
content_text = oci.generative_ai_inference.models.TextContent()
content_text.text = "この画像には何が映っていますか？"

# 画像コンテンツの作成
image_url = oci.generative_ai_inference.models.ImageUrl()
image_url.url = f"data:image/jpeg;base64,{encoded_image}"

content_image = oci.generative_ai_inference.models.ImageContent()
content_image.image_url = image_url

# ユーザーメッセージ作成（テキスト + 画像）
user_message = oci.generative_ai_inference.models.UserMessage()
user_message.content = [content_text, content_image]

# チャットリクエスト作成
chat_request = oci.generative_ai_inference.models.GenericChatRequest()
chat_request.api_format = oci.generative_ai_inference.models.BaseChatRequest.API_FORMAT_GENERIC
chat_request.messages = [user_message]
chat_request.max_tokens = 600
chat_request.temperature = 1
chat_request.frequency_penalty = 0
chat_request.presence_penalty = 0
chat_request.top_p = 0.75

# ChatDetailsに設定
chat_detail = oci.generative_ai_inference.models.ChatDetails()
chat_detail.serving_mode = oci.generative_ai_inference.models.OnDemandServingMode(
    model_id="meta.llama-3.2-90b-vision-instruct"
)
chat_detail.chat_request = chat_request
chat_detail.compartment_id = compartment_id

# リクエスト送信
chat_response = generative_ai_inference_client.chat(chat_detail)

# 結果出力
print("**************************Chat Result**************************")
print(chat_response.data.chat_response.choices[0].message.content[0].text)

```

```python
**************************Chat Result**************************
この画像には、イヌの「ゴールデン・レトリバー」の子供である「子犬」が映っています。子犬の体毛は、薄い黄色であることがわかります。子犬の体毛の色は、「ゴールデン・レトリバー」に多い「薄い黄色」であることがわかります。ただし、「ゴールデン・レトリバー」の体毛の色は、「薄い黄色」以外にも「中黄色」や「濃い黄色」であることがわかります。

子犬の目の色は、黒であることがわかります。子犬の顔の色は、薄い黄色であることがわかります。子犬の顔の形は、「ゴールデン・レトリバー」の特徴であることがわかります。

子犬の首には、青色のコリーやネクタイがあることがわかります。子犬の体毛は、みみなどは長いですが、ほとんどは短いことがわかります。子犬は、動物園やペットショップなどでは、「ゴールデン・レトリバー」の子犬であることがわかります。
```

以上、Generative AI Serviceのハンズオンでした。
