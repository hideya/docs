# Amazon SageMakerを用いた 簡単なDeep Learningアプリの作成 ハンズオン — DIY キット

「簡単に人工知能アプリを作る為のAmazon SageMakerクラウド・ハンズオン」で用いた
[資料をまとめたリポジトリ](https://github.com/maru-labo/docs/tree/master/20180512_sagemaker_handson)
の内容を元に、ハンズオンの内容を個人的に試せるように編集したものです。

ご参考：ハンズオンの募集ページ（募集は終了しました）： https://lab-kadokawa50.peatix.com/  

## 内容物

- `doodle.ipynb`: 落書き認識アプリを作る Jupyter ノートブックです

- `model.ipynb`: 上記ノートブックで用いたディープラーニングの実装について少し詳しい解説です

`src`ディレクトリ以下に、モデルの構築等を行う Python のソースコードが含まれています。

## 事前に必要なもの

- [Amazon Web Service](https://aws.amazon.com/) のアカウントと初歩的な利用経験
  （ご参考「[AWS アカウント作成の流れ](https://aws.amazon.com/jp/register-flow/)」）

- ニューラルネットワーク・深層学習に関する基礎的な知識
  （ご参考「[AIとは？AI（人工知能）とDeep Learning（深層学習）を簡単に説明](https://www.optim.cloud/blog/ai/ai-deeplearning/)」、
  「[これから始める人の為のディープラーニング基礎講座](https://www.slideshare.net/NVIDIAJapan/ss-71043984)」、
  [ディープラーニングに入門するためのリソース集と学習法](https://qiita.com/keitakurita/items/df3a07135c9cfad810c7)」）

- Jupyter Notebook に関する基礎的な知識
  （ご参考「[機械学習の現場で重宝する多機能WebエディタJupyter Notebookの基本的な使い方](https://goo.gl/PozicA)」）

## 使い方

1. このRepoの「**Clone or download**」から「**Download ZIP**」を選択し、ZIPをダウンロードします。
  `doodle-sagemaker-master.zip` がダウンロードされたことを確認してください。

1. AWS にサインインし、「**Amazon SageMaker**」を開きます。
  **Region**を、料金が安くて日本に近い「**米国西部 (オレゴン) US West (Oregon)**」にします
  （Tokyo も選択可能ですが、無料枠を超過した際の利用料が少しだけ高くなります）。
  SageMaker (region: オレゴン Oregon) の URL は
  [こちら](https://us-west-2.console.aws.amazon.com/sagemaker/home?region=us-west-2#/notebook-instances)
  になります。

1. SageMaker の Jupyter ノートブックインスタンスを生成し、必要なファイルをこれにアップロードします。
  まず、SageMakerのトップページの「**ノートブックインスタンスの作成 Create notebook instance**」ボタン、
  もしくは **ノートブック Notebook > ノートブックインスタンス Notebook instance > ノートブックインスタンスの作成 Create notebook instance** から、
  インスタンスを生成します。

1. 「**ノートブックインスタンス名 Notebook instance name**」には適当な名前を入力します。
  「**ノートブックインスタンスのタイプ Notebook instance type**」は「t2.medium」（最小・デフォルト）を選択します。
  このインスタンス・タイプには、申し込み後最初の 2 か月間は 250 時間の無料枠があります
  （2018年6月時点での情報です。
  ご参考：「[Amazon SageMaker の料金](https://aws.amazon.com/jp/sagemaker/pricing/)」）。
  その他もデフォルトのままでOKです。
  「**ノートブックインスタンスの作成 Create notebook instance**」ボタンをクリックします。

1. インスタンスの生成がはじまります。
  「**ノートブックインスタンス Notebook instances**」の一覧に、「**ステータス Status**」が「**Pending**」の
  生成したインスタンスが表示されるはずです。
  インスタンスが「**InService**」になるまで待ちます。2〜3分かかります。

1. 「**InService**」になったら「**アクション Actions**」から「**オープン Open**」を選択します。
  インスタンスで起動したノートブックのページが開きます。

1. 先ほどダウンロードしたZIPファイルをノートブックインスタンスにアップロードします。
  ノートブックのページ右上にある「**Upload**」をクリックし、`doodle-sagemaker-master.zip` を選択し、
  「**Upload**」ボタンをクリックします。
  アップロード後「**Files**」タブのリストにZIPファイルが表示されているのを確認します。

1. このZIPを解凍します。画面右上の「**New**」を押して、プルダウンメニューの一番下の「**Terminal**」を選び、
  ターミナルを開きます。ブラウザで新たなページが開かれ、その内にターミナルが表示されます。
  ここで、以下のコマンドを入力します。
  ```sh
  cd SageMaker
  unzip doodle-sagemaker-master.zip
  ```
  解凍が済んだらターミナルのページを閉じます。
  元のノートブックのページに戻り、「**Files**」のリストのページをリロードし、
  新たに `doodle-sagemaker-master` という名のフォルダができていることを確認します。

1. 本ハンズオンのメインとなるノートブック `doodle.ipynb` を開きます。
  **Files** のリストで、フォルダ `doodle-sagemaker-master` をクリックし、
  その中にある、`doodle.ipynb` をクリックします。
  ノートブックが開く際「Kernel not found」と表示されたら、
  `conda_tensorflow_p36` を選択し、「Set kernel」をクリックします。

1. 以降は、ノートブックの内容にしたがって、ハンズオンを進めてください。
