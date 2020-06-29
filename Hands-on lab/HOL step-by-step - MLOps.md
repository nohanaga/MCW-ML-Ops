![Microsoft Cloud Workshops](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png "Microsoft Cloud Workshops")

<div class="MCWHeader1">
MLOps
</div>

<div class="MCWHeader2">
ステップバイステップ式ハンズオン ラボ
</div>

<div class="MCWHeader3">
2020年6月
</div>

このドキュメントに記載されている情報 (URL や他のインターネット Web サイト参照を含む) は、将来予告なしに変更することがあります。別途記載されていない場合、このソフトウェアおよび関連するドキュメントで使用している会社、組織、製品、ドメイン名、電子メール アドレス、ロゴ、人物、場所、出来事などの名称は架空のものです。実在する商品名、団体名、個人名などとは一切関係ありません。お客様ご自身の責任において、適用されるすべての著作権関連法規に従ったご使用をお願いいたします。著作権法による制限に関係なく、マイクロソフトの書面による許可なしに、このドキュメントの一部または全部を複製したり、検索システムに保存または登録したり、別の形式に変換したりすることは、手段、目的を問わず禁じられています。ここでいう手段とは、複写や記録など、電子的、または物理的なすべての手段を含みます。

マイクロソフトは、このドキュメントに記載されている内容に関し、特許、特許申請、商標、著作権、またはその他の無体財産権を有する場合があります。別途マイクロソフトのライセンス契約上に明示の規定のない限り、このドキュメントはこれらの特許、商標、著作権、またはその他の知的財産権に関する権利をお客様に許諾するものではありません。

製造元名、製品名、URL は、情報提供のみを目的としており、これらの製造元またはマイクロソフトのテクノロジを搭載した製品の使用について、マイクロソフトは、明示的、黙示的、または法令によるいかなる表明も保証もいたしません。製造元または製品に対する言及は、マイクロソフトが当該製造元または製品を推奨していることを示唆するものではありません。掲載されているリンクは、外部サイトへのものである場合があります。これらのサイトはマイクロソフトの管理下にあるものではなく、リンク先のサイトのコンテンツ、リンク先のサイトに含まれているリンク、または当該サイトの変更や更新について、マイクロソフトは一切責任を負いません。リンク先のサイトから受信した Web キャストまたはその他の形式での通信について、マイクロソフトは責任を負いません。マイクロソフトは受講者の便宜を図る目的でのみ、これらのリンクを提供します。また、リンクの掲載は、マイクロソフトが当該サイトまたは当該サイトに掲載されている製品を推奨していることを示唆するものではありません。

© 2020 Microsoft Corporation. All rights reserved.

Microsoft および <https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx> (英語) に掲載されているその他の商標は、マイクロソフト グループ各社の商標です。その他すべての商標は、その所有者に帰属します。

**このドキュメントの内容**

<!-- TOC -->

- [MLOps ステップバイステップ式ハンズオン ラボ](#MLOps-ステップバイステップ式ハンズオン-ラボ)
  - [要約と学習目標](#要約と学習目標)
  - [概要](#概要)
  - [ソリューションのアーキテクチャ](#ソリューションのアーキテクチャ)
  - [前提条件](#前提条件)
  - [Before the hands-on lab](#before-the-hands-on-lab)
  - [演習 1: コンプライアンス分類モデルの作成と評価](#演習-1-コンプライアンス分類モデルの作成と評価)
    - [タスク 1: ノートブック環境をセットアップする](#タスク-1-ノートブック環境をセットアップする)
    - [タスク 2: ノートブックを使用して分類モデルを作成する](#タスク-2-ノートブックを使用して分類モデルを作成する)
  - [演習 2: モデルの登録](#演習-2-モデルの登録)
    - [タスク 1: Azure Machine Learning Python SDK を使用してモデルを登録する](#タスク-1-Azure-Machine-Learning-Python-SDK-を使用してモデルを登録する)
    - [タスク 2: Azure Machine Learning Studio からモデルを登録する](#タスク-2-Azure-Machine-Learning-Studio-からモデルを登録する)
  - [演習 3: Azure DevOps で新しいプロジェクトをセットアップする](#演習-3-Azure-DevOps-で新しいプロジェクトをセットアップする)
    - [タスク 1: 新しいプロジェクトを作成する](#タスク-1-新しいプロジェクトを作成する)
    - [タスク 2: GitHub リポジトリからクイックスタートコードをインポートする](#タスク-2-GitHub-リポジトリからクイックスタートコードをインポートする)
    - [タスク 3: ビルド YAML ファイルを更新する](#タスク-3-ビルド-YAML-ファイルを更新する)
    - [タスク 4: 新しいサービス接続を作成する](#タスク-4-新しいサービス接続を作成する)
  - [演習 4: ビルドパイプラインをセットアップして実行する](#演習-4-ビルドパイプラインをセットアップして実行する)
    - [タスク 1: ビルドパイプラインのセットアップ](#タスク-1-ビルドパイプラインのセットアップ)
    - [タスク 2: ビルドパイプラインの実行](#タスク-2-ビルドパイプラインの実行)
    - [タスク 3: ビルド作成物の確認](#タスク-3-ビルド作成物の確認)
    - [タスク 4: ビルド出力の確認](#タスク-4-ビルド出力の確認)
  - [演習 5: リリースパイプラインを設定する](#演習-5-リリースパイプラインを設定する)
    - [タスク 1: 空のジョブを作成する](#タスク-1-空のジョブを作成する)
    - [タスク 2: ビルド作成物を追加](#タスク-2-ビルド作成物を追加)
    - [タスク 3: Deploy and Test ステージに変数を追加する](#タスク-3-Deploy-and-Test-ステージに変数を追加する)
    - [タスク 4: Deploy and Test ステージのエージェントプールのセットアップ](#タスク-4-Deploy-and-Test-ステージのエージェントプールのセットアップ)
    - [タスク 5: Python バージョンの使用タスクの追加](#タスク-5-Python-バージョンの使用タスクの追加)
    - [タスク 6: インストール要件タスクの追加](#タスク-6-インストール要件タスクの追加)
    - [タスク 7: Webサービスの展開とテストタスクの追加](#タスク-7-Webサービスの展開とテストタスクの追加)
    - [タスク 8: デプロイトリガーの定義](#タスク-8-デプロイトリガーの定義)
    - [タスク 9: 継続的デプロイトリガーを有効にする](#タスク-9-継続的デプロイトリガーを有効にする)
    - [タスク 10: リリースパイプラインを保存する](#タスク-10-リリースパイプラインを保存する)
  - [演習 6: テストビルドおよびリリースパイプライン](#演習-6-テストビルドおよびリリースパイプライン)
    - [タスク 1: ソースコードを編集する](#タスク-1-ソースコードを編集する)
    - [タスク 2: ビルドパイプラインの監視](#タスク-2-ビルドパイプラインの監視)
    - [タスク 3: リリースパイプラインの監視](#タスク-3-リリースパイプラインの監視)
    - [タスク 4: リリースパイプライン出力の確認](#タスク-4-リリースパイプライン出力の確認)
  - [演習 7: デプロイされたソリューションのテスト](#演習-7-デプロイされたソリューションのテスト)
    - [タスク 1: デプロイをテストする](#タスク-1-デプロイをテストする)
  - [演習 8: デプロイされたモデルのパフォーマンスを検証する](#演習-8-デプロイされたモデルのパフォーマンスを検証する)
    - [タスク 1: デプロイされたモデルで App Insights とデータ収集をアクティブ化する](#タスク-1-デプロイされたモデルで-App-Insights-とデータ収集をアクティブ化する)
    - [タスク 2: Application Insights のテレメトリを確認する](#タスク-2-Application-Insights-のテレメトリを確認する)
    - [タスク 3: 収集したデータを確認する](#タスク-3-収集したデータを確認する)
  - [ハンズオンラボの後](#ハンズオンラボの後)
    - [タスク 1: ラボのリソースをクリーンアップする](#タスク-1-ラボのリソースをクリーンアップする)

<!-- /TOC -->

# MLOps ステップバイステップ式ハンズオン ラボ

## 要約と学習目標

このハンズオンラボでは、Trey Research 社がディープラーニングテクノロジーを活用して車両仕様のドキュメントをスキャンし、新しい規制のコンプライアンス問題を見つける方法を学びます。モデル形式を ONNX に標準化し、これが推論ランタイムコードを簡素化し、さまざまなモデルのプラグインを可能にし、幅広いランタイム環境をターゲットにする方法を観察します。最も重要なのは、ネイティブモデルより推論速度を向上させることです。DevOps パイプラインを構築して、モデルレジストリからの最新の最良のモデルの取得、Webアプリケーションのパッケージ化、Webアプリケーションのデプロイ、およびWebサービスの推論を調整します。最初のデプロイが成功した後、モデルおよびWebアプリケーションの両方を更新し、パイプラインを1回実行して、更新されたデプロイを実現します。また、モデルの展開後にモデルのパフォーマンスを監視する方法についても学習するため、Trey Research 社はパフォーマンスの問題に積極的に取り組むことができます。

このハンズオンラボの最後に、モデルに依存するすべてのアプリケーションコンポーネントを含め、ディープラーニングモデルを完全に運用するエンドツーエンドのソリューションをより適切に実装できるようになります。

## 概要

Trey Research Inc. は、メーカーに革新的なソリューションを提供します。彼らは、平凡で時間のかかるプロセスの自動化から、製造クライアントに新しい機会を提供する最先端のアプローチを提供することまで、幅広い範囲を実行できるメーカーの問題の特定と解決を専門としています。Trey Research は何十年にもわたってデータサイエンスとアプリケーション開発を専門としており、これまでは個別のユニットでした。彼らは、データサイエンスとアプリ開発の間のその場限りの相乗効果によって生み出される価値を見てきましたが、2つのユニットを1つにまとめることでアプローチを正式化し、イノベーションを運用するための標準化されたプロセスに従うことで、より大きな長期的な価値を解き放ちたいと考えています。

この複合イニシアチブの最初の取り組みとして、彼らは、ディープラーニングモデルのモデル作成とデプロイとともに、アプリケーションのライフサイクルのすべてのフェーズを網羅するディープラーニングを運用するためのプロセスを定義したいと考えています。この最初の概念実証（PoC）では、コンポーネントのコンプライアンスに焦点を当てたいと考えています。具体的には、ディープラーニングテクノロジーと自然言語処理（NLP）技術を活用して、車両仕様書をスキャンし、新しい規制へのコンプライアンスの問題を見つけようとしています。この最初のシナリオは自動車部品に焦点を当てていますが、このアプローチは、すべての製造業の顧客が扱う部品の在庫に関わるあらゆるシナリオに一般化できると考えています。部品の説明は、自由形式のテキストであり、ウェブアプリケーションを介して入力・管理されます。このWebアプリケーションは、認定された技術者によって入力された新しい部品の説明を受け取り、そのテキストに基づいて部品に適合または非適合のラベルを付けます。

また、作成したプロセス全体で、基礎となるモデルと Web アプリの両方を 1 つの統一されたパイプラインで更新できるようにしたいと考えています。また、デプロイ後にモデルのパフォーマンスを監視できるようにして、パフォーマンスの問題に積極的に対応できるようにしたいと考えています。

## ソリューションのアーキテクチャ

![The lab solution architecture as described by the text that follows.](media/architecture-overview.png 'Solution Architecture')

このラボで使用する全体的なアプローチは、Azure DevOps から継続的インテグレーションと継続的デリバリーの Azure パイプラインをオーケストレーションすることです。これらのパイプラインは、Azure Machine Learning SDK で作成された機械学習パイプラインを記述するアーティファクトへの変更によってトリガーされます。ラボでは、Azure Pipelines ビルドパイプラインを実行するモデルトレーニングスクリプトに変更を加えます。これにより、モデルがトレーニングされ、コンテナーイメージが作成されます。 次に、ビルドパイプラインで作成された Docker イメージを使用して、モデルを Web サービスとして AKS にデプロイする Azure パイプラインリリースパイプラインをトリガーします。本番環境に入ると、スコアリング Web サービスは、Application Insights と Azure Storage の組み合わせを使用して監視されます。

## 前提条件

1. Microsoft Azure サブスクリプションは、従量制または MSDN である必要があります。

   - 試用版サブスクリプションは機能しません。Azure リソースクォータの制限に関する問題が発生します。

   - アクセスが1つのリソースグループに制限されているサブスクリプションは機能しません。複数のリソースグループをデプロイする機能が必要になります。

2. Azure DevOps アカウント

## Before the hands-on lab

演習を続ける前に、[Before the hands-on lab setup guide](./Before&#32;the&#32;HOL&#32;-&#32;MLOps.md) を参照してください。

## 演習 1: コンプライアンス分類モデルの作成と評価

所要時間: 40分

この演習では、コンポーネントテキストを準拠または非準拠に分類するためのモデルを作成します。このチュートリアルでは、Azure Machine Learning ワークスペースのクラウドノートブックサーバーを使用して、Azure Machine Learning studio で利用できるインストール不要の事前構成済みエクスペリエンスを実現します。

> **Note:** 新しい [Azure Machine Learning studio](https://ml.azure.com) は、エンドツーエンドの機械学習ライフサイクルを管理するための新しい没入感のある体験を提供します。直接ログインするか、Azure Machine Learning ワークスペースの **概要** セクションにある **新しい Azure Machine Learning Studio を試して、今すぐ起動** オプションを選択して使用できます。

### タスク 1: ノートブック環境をセットアップする

1. GitHubで **Raw** ビューを選択し、**右クリック→名前を付けて保存**して、[**Deep Learning with Text.ipynb**](./notebooks/Deep&#32;Learning&#32;with&#32;Text.ipynb) ノートブックをコンピューターにダウンロードします。保存したファイルの拡張子が `.ipynb` であることを確認してください。これは、このラボで実行するためのステップノートです。

2. [Azure Machine Learning studio](https://ml.azure.com) にサインインします。

3. サブスクリプションと使用可能なワークスペースを選択します。

4. 左側のナビゲーションペインで **ノートブック** を選択します。

    ![In Azure Machine Learning Studio, Notebooks is selected from the left navigation pane.](media/notebook-00.png 'Open notebooks in Azure Machine Learning Studio')

5. **ユーザーファイル** セクションでフォルダを選択します。現在ログインしているユーザー名として名前を付ける必要があります。上部のメニューで **新しいフォルダを作成する** オプションを選択します。

    ![On the Notebooks screen, the current user is selected beneath the User Files section, and the Create New Folder icon is highlighted in the top toolbar.](media/notebook-01.png 'Create new notebooks folder')

6. フォルダ名を入力してください： `MCW-MLOps`.

7. トップメニューの **ファイルのアップロード** オプションを選択します。

    ![On the Notebooks screen, beneath user files, the folder of the current user is expanded displaying the folder that was created in the previous step. The Upload files icon is highlighted in the top toolbar.](media/notebook-02.png 'Upload notebook to the workspace file share')

8. ダウンロードしたノートブック、**Deep Learning with Text.ipynb** を参照し、ターゲットフォルダーとして **MCW-MLOps** フォルダーを選択します。次に、**アップロード** を選択します。

9. ノートブックを選択します。 **+新しいコンピューティング** を選択して、コンピューティングインスタンスVMを作成します。

    ![On the Notebooks screen, beneath user files, the folder of the current user is expanded along with the folder that was created in step 6. Inside this folder the Notebook that we uploaded in the previous step is displayed and is selected. On the Compute screen to the right, the + New Compute button is highlighted in the top taskbar.](media/notebook-03.png 'Create new compute instance')

10. ノートブックで実行する新しいコンピューティングインスタンスを作成するために必要なデータを提供します。

    a. コンピューティング名： `mlops-compute`。VM を作成するときに、名前を指定します。名前は 2〜16 文字にする必要があります。有効な文字は、英数字、および - (ハイフン)であり、Azure サブスクリプション全体で一意である必要もあります。

    b. 仮想マシンタイプ：CPU（中央処理装置）

    c. 仮想マシンサイズ: **Standard_D3_v2**.

    d. 次に **作成** を選択します。VM のセットアップには約5分かかります。

    ![The New Compute Instance form is displayed populated with the preceding values.](media/notebook-04.png 'Configure the new compute instance')

    > **Note**: VM が使用可能になると、上部のツールバーに表示されます。

11. アップロードした *Deep Learning with Text.ipynb** ノートブックを選択したら、 **Edit** ドロップダウンを選択し、 **Edit in Jupyter** を選択します。新しいブラウザウィンドウが開きます。

    ![On the Notebooks screen, the Deep Learning with Text Notebook is selected. On the Compute screen to the right, a drop down list shows the compute currently running for the notebook, and in the taskbar the Edit option is expanded with the options Edit in Jupyter and Edit in JupyterLab.](media/notebook-05.png 'Edit the notebook in Jupyter')

12. カーネルの選択を求められたら、**Python 3.6-Azure ML** を選択します。

    ![A Kernel not found dialog is displayed with Python 3.6 - Azure ML selected from a drop down list. A Set Kernel button is available to confirm the kernel selection.](media/notebook-06.png 'Select Kernel version')

### タスク 2: ノートブックを使用して分類モデルを作成する

1. ノートブック内の指示に従って、ラボを完了してください。

2. [Azure Machine Learning Studio](https://ml.azure.com) に戻り、**Notebooks** の ** MCW-MLOps** フォルダーの下で、**model** フォルダーに移動してダウンロードします。**model.onnx** ファイルをローカルディスクにコピーします。次の演習では、ダウンロードしたモデルファイルを使用します。

   > **Note**: ダウンロードしたファイル名を **utf-8 model.onnx** または **notebooks_model_model.onnx** に変更した場合は、ファイルの名前を `model.onnx`に戻します。

   > **Note**: **model.onnx** ファイルは、前のステップ（ステップ1）でのノートブックの実行中に生成されます。ノートブックを実行するときは、実行が成功し、ファイルが正しく作成されていることを確認してください。

## 演習 2: モデルの登録

所要時間: 15分

この演習では、モデルバージョンを管理するためのアプローチ、実験実行との関連付け、プログラムおよび　[Azure Machine Learning studio](https://ml.azure.com)　経由でモデルを取得する方法について学びます。

### タスク 1: Azure Machine Learning Python SDK を使用してモデルを登録する

1. GitHubで **Raw** ビューを選択して [**Register Model.ipynb**](./notebooks/Register&#32;Model.ipynb) ノートブックをコンピューターにダウンロードし、**右クリック→名前を付けて保存** します。保存したファイルの拡張子が `.ipynb`であることを確認してください。これは、この演習で実行するステップバイノートブックです。

2. スタジオで、 **ノートブック** に移動し、上部のメニューで **ファイルをアップロード** オプションを選択します。

3. ローカルコンピューターを参照して、ダウンロードしたノートブックの **Register Model.ipynb** を探し、ターゲットフォルダーとして **MCW-MLOps** を選択します。次に、**アップロード** を選択します。

4. ノートブック `Register Model.ipynb` を選択します。上部のバーで、ノートブックの実行に使用する **mlops-compute** コンピューティングインスタンスを選択します。**編集** ドロップダウンを選択し、**Jupyterで編集** を選択します。すると新しいブラウザウィンドウが開きます。

5. ノートブック内の指示に従って、ラボを完了してください。

6. [Azure Machine Learning studio](https://ml.azure.com) に直接移動するか、[Azure ポータル](https://portal.azure.com) 経由で移動します。ノートブックから作成した Azure Machine Learning ワークスペースを必ず選択してください。**Models** セクションを開き、登録されているモデルの **バージョン1** を確認します： `compliance-classifier`。

    ![In Azure Machine Learning Studio, from the left menu, Models is selected. In the Model List, the compliance-classifier with the version of 1 is highlighted.](media/model-registry-01.png 'Registered Model: compliance-classifier')

### タスク 2: Azure Machine Learning Studio からモデルを登録する

1. [Azure Machine Learning studio](https://ml.azure.com) で、 **モデル** セクションを開き、**+モデルの登録** を選択します。

    ![In Auzre Machine Learning Studio, Models is selected in the left menu. In the taskbar of the Model list, the + Register Model button is selected.](media/model-registry-02.png 'Register Model in Azure Machine Learning studio')
  
2. **モデルの登録** ダイアログに次の入力を入力し、 **登録** を選択します。

    a. 名前: `compliance-classifier`

    b. 説明: `自動車コンポーネントの説明を準拠または非準拠として分類するためのディープラーニングモデル。`

    c. モデルフレームワーク: **TensorFlow**

    d. モデルフレームワークバージョン: `2.0`

    e. モデルファイル: ローカルディスクから `model.onnx` ファイルを選択します。

    ![The Register a Model form is displayed populated with the preceding values.](media/model-registry-03.png 'Register a model Dialog')

3. **Models** セクションに移動し、登録済みモデル **compliance-classifier** が **バージョン2** であることを確認します。

    ![The Model list is displayed showing two rows containing both versions of the compliance-classifier model. Version 2 of the compliance-classifier model is highlighted in the list.](media/model-registry-04.png 'Registered Model: compliance-classifier version 2')

## 演習 3: Azure DevOps で新しいプロジェクトをセットアップする

所要時間: 20分

### タスク 1: 新しいプロジェクトを作成する

1. [Azure DevOps](http://dev.azure.com) にサインインします。

2. **+ 新規プロジェクト** を選択します。

    ![In the Azure DevOps screen, the + New project button is selected.](media/devops-project-01.png 'Create new project')

3. プロジェクト名： `mlops-quickstart`を入力し、**作成** を選択します。

    ![The Create new project dialog is shown populated with the value above. Visibility is set to Private, and the Create button is highlighted.](media/devops-project-02.png 'Create New Project Dialog')

### タスク 2: GitHub リポジトリからクイックスタートコードをインポートする

1. 新しいプロジェクト内：

   a. 左側のナビゲーションバーから **Repos** を選択します。

   b. コンテンツセクションから **インポート** を選択します。

    ![In Azure DevOps, Repos is selected from the left menu. In the mlops-quickstart screen the Import button is selected in the Import a repository section.](media/devops-project-03.png 'Azure DevOps Repos')

2. 次の GitHub URL を指定します： `https://github.com/solliancenet/mcw-mlops-starter-v2`を選択し、 **インポート** を選択します。これにより、クイックスタートに必要なコードがインポートされます。

    ![In the Import a Git repository dialog, the Clone URL is populated with the value indicated above and the Import button is selected.](media/devops-project-04.png 'Import a Git repository dialog')

    > **Note**: リポジトリのインポート中にエラーが発生した場合は、プレビュー機能→**新しいReposランディングページ** を無効にして、GitHub リポジトリを古い UI からインポートしてください（以下のステップ#3、#4、および#5を参照）。

3. [オプション] **アカウント設定、プレビュー機能** を選択します。

    ![On the mlops-quickstart repo page, Settings is expanded in the taskbar and the Preview features item is highlighted.](media/preview_features-01.png 'Preview features')

4. [オプション] プレビュー機能のリストから、プレビュー機能 **新しいReposランディングページ** を無効にします。

   ![A list of preview features is displayed highlighting the New Repos landing pages features.](media/preview_features-02.png 'Disable New Repos landing pages')

5. [オプション] 上記の手順1を繰り返して、古い UI から GitHub リポジトリをインポートします。

### タスク 3: ビルド YAML ファイルを更新する

1. **azure-pipelines.yml** ファイルを選択して開きます。

2.  **編集** を選択し、次の変数を更新します：**resourcegroup**、および **workspace**。独自の Azure サブスクリプションを使用している場合は、使用する名前を指定してください。環境が提供されている場合は、以下の値のXXXXXを一意の識別子に置き換えてください。

    ![In the left menu, beneath Repos, the Files item is selected. In the files list, azure-pipelines.yml is selected. In the editor pane, the contents of the file are displayed with the resource group and workspace variables highlighted. The Edit button is selected in the top toolbar.](media/devops-build-pipeline-01.png 'Edit Build YAML file')

3.  **コミット** を選択して変更を保存し、[コミットのプロパティ]ダイアログでもう一度 **コミット** を選択します。

    ![The content of azure-pipelines.yml is updated and the Commit button is selected in the top taskbar.](media/devops-build-pipeline-02.png 'Commit Build YAML file')

### タスク 4: 新しいサービス接続を作成する

1. 左側のナビゲーションから、 **プロジェクト設定** を選択し、 **サービス接続** を選択します。

    ![In the left menu, Project settings is selected. In the Project Settings list, Service connections is selected. In the Create your first service connection screen, the Create service connection button is selected.](media/devops-build-pipeline-03.png 'Service Connections')

2.  **サービス接続の作成** 、**Azure リソースマネージャー**、**次へ** の順に選択します。

    ![In the New service connection dialog, Azure Resource Manager is selected from the list. The Next button is selected.](media/devops-build-pipeline-04.png 'Azure Resource Manager')

3.  **サービスプリンシパル（自動）** を選択して、 **次へ** を選択します。

    ![In the New service connection dialog, under Authentication method, Service principal (automatic) is selected. The Next button is selected.](media/devops-build-pipeline-05.png 'Service principal authentication')

4. **新しいAzureサービス接続** ダイアログボックスで次の情報を入力し、**保存** を選択します。

    a. **スコープレベル**: **Machine Learning Workspace**

    b. **サブスクリプション**: 使用するAzureサブスクリプションを選択します。

    > **Note**: アカウントがアクセスできるさまざまなサブスクリプションの数によっては、**サブスクリプション** ドロップダウンに利用可能なサブスクリプションが表示されるまでに最大30秒かかる場合があります。

    c. **リソースグループ**: この値は、**azure-pipelines.yml** ファイルで指定した値と一致する必要があります。

    d. **Machine Learning Workspace**: この値は、**azure-pipelines.yml** ファイルで指定した値と一致する必要があります。

    e. **サービス接続名**: `quick-starts-sc`

    f. **セキュリティ**: すべてのパイプラインへのアクセス許可の付与がチェックされています。

    ![The New Azure service connection form is populated with the values outlined above. The Save button is selected.](media/devops-build-pipeline-06.png 'Add an Azure Resource Manager service connection dialog')

    >**Note**: **Machine Learning Workspace** を選択できない場合は、次の手順を実行します。

    a. [新しい Azure サービス接続]ダイアログを終了します。
    
    b. Web ブラウザーを更新または再ロードします。
    
    c. 上記の手順1〜3を繰り返します。
    
    d. ステップ4で、[スコープレベル] を **サブスクリプション** に変更し、**リソースグループ** を選択します。
    
    e. サービス接続には `quick-starts-sc` という名前を付けてください。
    
    f. すべてのパイプラインにアクセス許可を付与します。

## 演習 4: ビルドパイプラインをセットアップして実行する

所要時間: 30分

### タスク 1: ビルドパイプラインのセットアップ

1. 左側のナビゲーションから **パイプライン→パイプライン** を選択し、**パイプラインを作成** を選択します。

    ![In the left menu, the Pipelines item is expanded with the Pipelines item selected. In the content pane, the Create pipeline button is highlighted.](media/devops-build-pipeline-07.png 'Create Build Pipeline')

2. コードリポジトリとして　**Azure Repos Git** を選択します。

    ![On the Connect tab of your pipeline screen, Azure Repos Git is selected beneath the Where is your code? prompt.](media/devops-build-pipeline-08.png 'Repository Source')

3. リポジトリとして **mlops-quickstart** を選択します。

    ![On the Select tab of your pipeline screen, beneath the Select a repository section, the mlops-quickstart repository is selected.](media/devops-build-pipeline-09.png 'Select Repository')

4. YAML ファイルを確認します。

    ビルドパイプラインには以下の4つの重要なステップがあります。

    a. ワークスペースにフォルダーを添付して実験します。このコマンドは、Azure Machine Learning ワークスペースとの通信に使用される **config.json** ファイルを含む **azureml** サブディレクトリを作成します。以降のすべての手順では、**config.json** ファイルを使用してワークスペースオブジェクトをインスタンス化します。

    b. AML Compute ターゲットを作成して、モデルトレーニングとモデル評価のためにマスターパイプラインを実行します。

    c. マスターパイプラインを実行します。マスターパイプラインには2つのステップがあります。（1）機械学習モデルをトレーニングし、（2）トレーニングされた機械学習モデルを評価します。評価ステップでは、新しいモデルのパフォーマンスが現在デプロイされているモデルよりも優れているかどうかを評価します。新しいモデルのパフォーマンスが向上した場合、評価手順では、展開用の新しいイメージを作成します。評価ステップの結果は、**eval_info.json** というファイルに保存され、リリースパイプラインで使用できるようになります。マスターパイプラインのコードとそのステップは、**aml_service/pipelines_master.py**、**scripts/train.py**、および **scripts/evaluate.py** で確認できます。

    d. ビルド作成物を公開します。**リポジトリのスナップショット**、**config.json**、および **eval_info.json** ファイルはビルド作成物として公開されるため、リリースパイプラインで利用できます。

    ![On the Review tab of your pipeline screen, the contents of azure-pipelines.yml is displayed.](media/devops-build-pipeline-10.png 'Build pipeline YAML')

### タスク 2: ビルドパイプラインの実行

1. **実行** を選択して、ビルドパイプラインの実行を開始します。

    ![On the Review tab of your pipeline screen, the contents of azure-pipelines.yml is displayed. The Run button is selected from the top taskbar.](media/devops-build-pipeline-11.png 'Run Build Pipeline')

2. ビルドの実行を監視します。最初の実行のビルドパイプラインの実行には、約25分かかります。

    ![A build pipeline run summary screen is displayed indicating it was manually triggered. A single job is selected in the Jobs section with a status of Success.](media/devops-build-pipeline-12.png 'Monitor Build Pipeline')

3. **ジョブ** を選択して、ビルドパイプラインの実行の詳細なステータスを監視します。

    ![In the Jobs screen, the Job that was selected in the previous step is expanded displaying multiple steps. To the right a summary of the run is displayed.](media/devops-build-pipeline-13.png 'Monitor Build Pipeline Details')

### タスク 3: ビルド作成物の確認

1. ビルドは `devops-for-ai` という名前の作成物を公開します。作成物の内容を確認するには、**1件公開済み** を選択します。

    ![On the build pipeline run summary, in the table outlining the manual run, the 1 published beneath the related column is selected.](media/devops-build-pipeline-14.png 'Build Artifacts')

2. **outputs→eval_info.json** を選択し、ダウンロード矢印を選択します。`eval_info.json` は **モデル評価** ステップからの出力です。評価ステップからの情報は、リリースパイプラインでモデルをデプロイするために使用されます。前の画面に戻るには、戻る矢印を選択します。

    ![On the Artifacts screen, a list of files are displayed. The outputs folder is expanded and the eval-info.json file download button is selected. The back arrow is selected a the top of the screen to navigate back to the previous page.](media/devops-build-pipeline-15.png 'Download JSON file')

3. **eval_info.json** を json ビューアまたはテキストエディタで開き、情報を確認します。json の出力には、モデルが評価ステップに合格したかどうか（**deploy_model**：**true** または **false**）、作成されたイメージの名前とID（**image_name** および **image_id**）をデプロイします。

    ![The contents of the eval_info.json file is displayed in Visual Studio.](media/devops-build-pipeline-16.png 'Eval Info JSON File')

### タスク 4: ビルド出力の確認

1. [Azure Machine Learning studio](https://ml.azure.com) に直接または [Azureポータル](https://portal.azure.com) からログインします。以前にノートブックから作成した Azure Machine Learning ワークスペースを必ず選択してください。**Models** セクションを開き、登録されている **compliance-classifier** モデルのバージョンを確認します。最新バージョンは、前のタスクで実行したビルドパイプラインによって登録されたバージョンです。

    ![In Azure Machine Learning Studio, models is selected in the left menu. A list of multiple versions of the compliance-classifier model is displayed in the Model list table with the largest version of the model highlighted in the table.](media/devops-build-outputs-01.png 'Registered Models in Azure Machine Learning studio')

2. モデルの最新バージョンを選択して、そのプロパティを確認します。**build_number** タグは、登録されたモデルを、それを生成した Azure DevOps ビルドにリンクします。

    ![The model screen for the latest version of the compliance-classifier is displayed with the Build_Number tag highlighted.](!media/../media/devops-build-outputs-02.png 'Registered model details and Build_Number tag')

3. **Datasets** セクションを開き、登録されているデータセットのバージョンを確認します：**connected_car_components**。最新バージョンは、前のタスクで実行したビルドパイプラインによって登録されたバージョンです。

    ![In Azure Machine Learning Studio, Datasets is selected from the left menu. The Datasets screen displays a list of datasets on the Registered datasets tab. The connected_car_components dataset is selected in the table with its tag indicating the build number matching the value from the previous step.](media/devops-build-outputs-03.png 'Registered Datasets in Azure Machine Learning studio')

4. データセットの最新バージョンを選択して、そのプロパティを確認します。データセットバージョンを、それを生成した Azure DevOps ビルドにリンクする **build_number** タグに注意してください。

    ![The registered dataset version properties screen is displayed with a tag that indicates the build_number.](medial/../media/devops-build-outputs-04.png 'Registered dataset details in Azure Machine Learning studio')

5. **モデル** を選択して、データセットを参照する登録済みモデルのリストを表示します。

    ![A list of registered models that reference the selected dataset is displayed.](media/devops-build-outputs-05.png 'Registered dataset model references in Azure Machine Learning studio')

6. [Azure ポータル](https://portal.azure.com) にログインし、**リソースグループ→ワークスペース→イメージ** セクションを開いて、ビルドパイプライン中に作成されたデプロイメントイメージ `compliance-classifier-image` を確認します。

    ![In the Images resource page, Images is selected from the left menu, and a list of Images is displayed. Multiple compliance-classifier-image images are shown with their associated versions. The latest version image is highlighted in the table.](media/devops-build-outputs-06.png 'Images in Azure Portal')

## 演習 5: リリースパイプラインを設定する

所要時間: 20分

### タスク 1: 空のジョブを作成する

1. Azure DevOps に戻り、**パイプライン、リリース** に移動して **新しいパイプライン** を選択します。
 
    ![In Azure DevOps, the Pipelines item is expanded in the left menu with the Releases item selected. In the content pane, a message indicates No release pipelines found and the New pipeline button is selected.](media/devops-release-pipeline-01.png 'New Release Pipeline')

2. **空のジョブ** を選択します。

    ![In the Select a template dialog, the Empty job item is selected above the list featured templates.](media/devops-release-pipeline-02.png 'Select a template: Empty job')

3. ステージ名: `Deploy and Test` を指定して、ダイアログを閉じます。

    ![On the Stage dialog, the Stage name textbox is populated with Deploy and Test. The close button at the top of the dialog is selected.](media/devops-release-pipeline-03.png 'Deploy and Test Stage')

### タスク 2: ビルド作成物を追加

1. **+ Add an artifact** を選択します。

    ![In the New release pipeline screen, on the Pipeline tab, the + Add a new artifact item is selected within the Artifacts tile.](media/devops-release-pipeline-04.png 'Add an artifact')

2. **ソースタイプ**: **Build**, **ソース (build pipeline)**: **mlops-quickstart** を選択します。

    > **Note**: mlops-quickstart が devops-for-ai という名前のビルド作成物を公開することを示すメモを確認してください。

    最後に、**Add** を選択します。

    ![The Add an artifact dialog form is populated with the aforementioned values. The Add button is selected.](media/devops-release-pipeline-05.png 'Add a build artifact')

### タスク 3: Deploy and Test ステージに変数を追加する

1. **View stage tasks** リンクを開きます。

    ![On the New release pipeline screen, within the Deploy and Test tile, the View stage tasks link is selected.](media/devops-release-pipeline-06.png 'View Stage タスクs')

2. **Variables** タブを開きます。

    ![On the New release pipeline screen, the Variables tab is selected.](media/devops-release-pipeline-07.png 'Release Pipeline Variables')

3. 4つのパイプライン変数を名前と値のペアとして追加し、**保存** を選択します（**保存** ダイアログのデフォルト値を使用します）：

    a. **Name**: `aks_name` **Value**: `aks-cluster01`

    b. **Name**: `aks_region` **Value**: `eastus`

    c. **Name**: `service_name` **Value**: `compliance-classifier-service`

    d. **Name**: `description` **Value**: `"Compliance Classifier Web Service"`

    > **Note**: **description** の値をダブルクォーテーションで囲みます。
    

    > **Note**:
    >   - 変数のスコープを **Deploy and Test** ステージに維持します。
    >   -Azure リージョンの名前は、以前に Azure Machine Learning ワークスペースを作成するために使用されたものと同じである必要があります。

      ![On the New release pipeline screen, the Variables tab is selected, and the Pipeline variables item is selected from a list of variable types. The list of Pipeline variables is displayed showing the variables that were just created.](media/devops-release-pipeline-08.png 'Add Pipeline Variables')

### タスク 4: Deploy and Test ステージのエージェントプールのセットアップ

1. **Tasks** タブを開きます。

    ![On the New release pipeline screen, the Tasks tab is selected.](media/devops-release-pipeline-09.png 'Pipeline Tasks')

2. **エージェントジョブ** を選択し、**エージェントプール** を `Azure Pipelines` に設定し、**エージェント仕様** を `ubuntu-16.04` に変更します。

    ![On the New release pipeline screen, Tasks tab, the Agent job is selected. The Agent job details form is populated with the aforementioned values.](media/devops-release-pipeline-10.png 'Agent Job Setup')

### タスク 5: Python バージョンの使用タスクの追加

1. **タスクをエージェントジョブに追加**（[**+**] ボタン）を選択し、`Use Python Version` を検索して、**追加** を選択します。

    ![On the New release pipeline screen, the Tasks tab is selected. Agent job is displayed in the list of tasks. The + button is selected in the Agent job tile. The Add tasks pane is displayed with Use Python version entered in the search box, and the Use Python version search result is highlighted with its Add button selected.](media/devops-release-pipeline-11.png 'Add Use Python Version Task')

2. **表示名：** `Use Python 3.6` と **Version spec：** ` 3.6` を入力します。

    ![The Use Python version form is displayed populated with the preceding values.](media/devops-release-pipeline-12.png 'Use Python Version Task Dialog')

### タスク 6: インストール要件タスクの追加

1. **タスクをエージェントジョブに追加**（[**+**] ボタン）を選択し、 `Bash` を検索して、**追加** を選択します。

    ![On the New release pipeline screen, the Tasks tab is selected. A list of tasks includes the Agent job that has a Use Python 3.6 task. The + button is selected in the Agent job tile, and in the Add tasks form, Bash is entered into the search text box and the Bash item is highlighted in a list of search results with its Add button selected.](media/devops-release-pipeline-13.png 'Add Bash Task')

2. **表示名：** `Install Requirements` を入力し、**スクリプトパスを参照...** を選択して **スクリプトパス** を入力します。

    ![On the New release pipeline screen, the Tasks tab is selected. A list of tasks is displayed below the Agent job. The Install requirements job is selected from this list. In the Bash form, fields are populated with the preceding values.](media/devops-release-pipeline-14.png 'Bash Task Dialog')

3. **Linked artifacts/_mlops-quickstart (Build)/devops-for-ai/environment_setup** に移動し、**install_requirements.sh** を選択します。

    ![A Select a file or folder dialog is displayed showing the location hierarchy to the install_requirements.sh file. The OK button is selected.](media/devops-release-pipeline-15.png 'Select Path Dialog')

4. **詳細設定** を展開し、**作業ディレクトリを参照...** を選択して、**作業ディレクトリ** を入力します。

    ![On the Bash form, the Advanced section is expanded. The ellipsis button is selected next to the Working Directory textbox.](media/devops-release-pipeline-16.png 'Bash Task - Advanced Section')

5. **Linked artifacts/_mlops-quickstart (Build)/devops-for-ai** に移動し、**environment_setup** を選択します。

    ![In the Select a file or folder dialog, the location hierarchy is displayed to the environment_setup folder.](media/devops-release-pipeline-17.png 'Select Path Dialog')

### タスク 7: Webサービスの展開とテストタスクの追加

1. **タスクをエージェントジョブに追加** (**+** ボタン)を選択し、`Azure CLI` を検索して、**追加**を選択します。

    ![In the New release pipeline screen, the Tasks tab is selected. In the list of Tasks, in the Agent job tile, the + button is selected. In the Add tasks form, Azure CLI is entered into the search box, and the Azure CLI search result is highlighted with its Add button selected.](media/devops-release-pipeline-18.png 'Azure CLI Task')

2. Azure CLI タスクに関する次の情報を提供します。

    a. **Task version**: `1.*`

    b. **Display name**: `Deploy and Test Webservice`

    c. **Azure subscription**: `quick-starts-sc`

    > **Note**: これは、演習1のタスク4で作成したサービス接続です。

    d. **Script Location**: `Inline script`

    e. **Inline Script**: `python aml_service/deploy.py --service_name $(service_name) --aks_name $(aks_name) --aks_region $(aks_region) --description $(description)`

    ![On the Tasks tab of the New release pipeline screen, the Deploy and Test Webservice task is selected beneath the Agent job item. The Azure CLI form is populated with the preceding values.](media/devops-release-pipeline-19.png 'Azure CLI Task Dialog')

3. **Advanced** を展開し、**Working Directory:** に `$(System.DefaultWorkingDirectory)/_mlops-quickstart/devops-for-ai` と入力します。

    ![In the Azure CLI form, the Advanced section is expanded and the Working Directory field is populated with the specified value.](media/devops-release-pipeline-20.png 'Azure CLI Task - Working Directory')

> **Note**: `aml_service/deploy.py`のコードを確認してください。このスクリプトは、各トレーニング済みモデルに関連付けられている `eval_info.json` ファイルを使用することにより、新しいトレーニング済みモデルのパフォーマンスが現在デプロイされているモデルよりも優れているかどうかを判断できます。新しいモデルの方がパフォーマンスが優れていると判断した場合、**Azure Kubernetes Service(AKS)** クラスターの本番環境に新しいモデルをデプロイします。

### タスク 8: デプロイトリガーの定義

1. **Pipeline** タブに移動し、**Deploy and Test** ステージの **Pre-deployment conditions** を選択します。

2. **After release** を選択します。

    ![In the New release pipeline screen, the Pipelines tab is selected. Within the Stages tile, the Pre-deployment Condition item is selected in the Deploy and Test stage tile. The Pre-deployment conditions form is displayed with the Triggers section expanded. After release is selected as the trigger.](media/devops-release-pipeline-21.png 'Pre-deployment Conditions Dialog')

3. ダイアログを閉じます。

### タスク 9: 継続的デプロイトリガーを有効にする

1. `_mlops-quickstart` 作成物の、**Continuous deployment trigger** を選択します。

2. **「新しいビルドが利用可能になるたびにリリースを作成します」** を有効にします。

    ![In the New release pipeline screen, the Pipelines tab is selected. Within the Artifacts tile, the Continuous deployment trigger option is selected on the _mlops-quickstart tile. The Continuous deployment trigger form is displayed indicating that it is Enabled.](media/devops-release-pipeline-22.png 'Continuous Deployment Trigger Dialog')

3. ダイアログを閉じます。

### タスク 10: リリースパイプラインを保存する

1. パイプラインの名前として、`mlops-quickstart-release` 入力します。

2. **Save** を選択します。(**保存** ダイアログのデフォルト値を使用します).

    ![In the header of the New pipeline screen, the pipeline name is set to mlops-quickstart-release, and the Save button is selected from the top taskbar.](media/devops-release-pipeline-23.png 'Save')

## 演習 6: テストビルドおよびリリースパイプライン

所要時間: 30分

### タスク 1: ソースコードを編集する

1. **Repos -> Files -> scripts -> `train.py`** に移動します。

2. `train.py` を**編集**します。

3. オプティマイザの **学習率（lr）** を **0.1** から **0.001** に変更します。

4. トレーニング**エポック**の数を **3** から **5** に変更します。

5. **Commit** を選択します。

    ![In Azure DevOps, the Repos item is expanded in the left menu with Files selected. In the file list, beneath the expanded scripts folder, train.py is selected. The train.py contents is displayed with the source code changes indicated in the previous steps in place. The Commit button is selected in the top toolbar.](media/devops-test-pipelines-01.png 'Edit Train.py')

6. コメントに、`Improving model performance: changed learning rate.` と入力し、**Commit** します。

    ![On the Commit dialog, the comment above is entered and the Commit button is selected.](media/devops-test-pipelines-02.png 'Commit - Comment')

### タスク 2: ビルドパイプラインの監視

1. **Pipelines→Pipelines** へ移動します。ソースコードの変更により、CI ビルドがトリガーされることを確認します。

   ![In Azure DevOps, Pipelines is selected below the Pipeline item in the left menu. In the Pipelines list, the Recent tab is selected. A currently running pipeline is shown and selected in this list.](media/devops-test-pipelines-03.png 'Pipelines - pipelines')

2. パイプライン実行を選択し、パイプラインステップを監視します。パイプラインは 18〜25 分間実行されます。ビルドパイプラインが正常に完了したら、次のタスクに進みます。

   ![In the Job details screen, the progress of the pipeline run is shown. Every step shows success.](media/devops-test-pipelines-04.png 'Build Pipeline Steps')

### タスク 3: リリースパイプラインの監視

1. **Pipelines→Releases** に移動します。ビルドパイプラインが正常に完了すると、リリースパイプラインが自動的にトリガーされることを確認します。図に示すように選択して、パイプラインログを表示します。

   ![In Azure DevOps, on the left menu, Pipelines is expanded and the Releases item is selected. The ml-ops-quickstart-release screen is displayed with the Releases tab selected. A release named Release-1 is highlighted with a button in the Stage column that is used to view the pipeline logs.](media/devops-test-pipelines-05.png 'Pipelines - Releases')

2. リリースパイプラインは約 15 分間実行されます。リリースパイプラインが正常に完了したら、次のタスクに進みます。

### タスク 4: リリースパイプライン出力の確認

1. パイプラインログビューから、**Deploy and Test Webservice** タスクを選択して詳細を表示します。

    ![In the Release-1, Deploy and Test Stage results, A list of tasks related to Agent job is displayed. The Deploy and Test Webservice task is selected from the list.](media/devops-test-pipelines-06.png 'Pipeline Logs')

2. デプロイされたWebサービスの**スコアリング URI** と **API キー**を確認します。**演習8** の**スコアリング URI** と **API キー**の両方を書き留めてください。

    ![The Deploy and Test Webservice task logs are displayed. Within the logs the Webservice URI and Webservice API Key are highlighted.](media/devops-test-pipelines-07.png 'Deploy and Test Webservice Task Logs')

3. Azure Machine Learning Studio にログインします。 **Endpoints** セクションを開き、デプロイされたWebサービスを確認します。
**compliance-classifier-service**

    ![In Azure Machine Learning Studio, the Endpoints item is selected from the left menu. In the list of Endpoints, the compliance-classifier-service is selected.](media/devops-test-pipelines-08.png 'Azure Machine Learning studio - Workspace, Deployments')

## 演習 7: デプロイされたソリューションのテスト

所要時間: 15分

この演習では、アプリケーションの最初のリリースが機能することを確認します。

### タスク 1: デプロイをテストする

1. [**Test Deployment.ipynb**](./notebooks/Test&#32;Deployment.ipynb) ノートブックをあなたのローカルコンピューターにダウンロードします。GitHub で**Raw** ビューを選択し、**右クリック+名前を付けて保存**します。保存したファイルの拡張子が `.ipynb` であることを確認してください。これは、この演習で実行するステップバイノートブックです。

2. Azure Machine Learning Studio で、**ノートブック**に移動し、上部のメニューで**ファイルのアップロード**オプションを選択します。

3. ローカルコンピューターを参照してダウンロードしたノートブック **Test Deployment.ipynb** を探し、ターゲットフォルダーとして **MCW-MLOps** フォルダーを選択します。次に、**アップロード**を選択します。

4. 上部のバーで、ノートブックの実行に使用する **mlops-compute** コンピューティングインスタンスを選択します。**編集**ドロップダウンを選択し、**Jupyterで編集**を選択します。新しいブラウザウィンドウが開きます。

5. ノートブックにデプロイされた Web サービスの**スコアリング URI** および **API キー**の値を提供する必要があることに注意してください。

6. ノートブック内の指示に従って、タスクを完了します。

## 演習 8: デプロイされたモデルのパフォーマンスを検証する

所要時間: 15分

この演習では、デプロイされたモデルのパフォーマンスを監視する方法を学びます。

### タスク 1: デプロイされたモデルで App Insights とデータ収集をアクティブ化する

1. [**Model Telemetry.ipynb**](./notebooks/Model&#32;Telemetry.ipynb) ノートブックをあなたのローカルコンピューターにダウンロードします。GitHub で**Raw** ビューを選択し、**右クリック+名前を付けて保存**します。保存したファイルの拡張子が `.ipynb` であることを確認してください。これは、この演習で実行するステップバイノートブックです。

2. Azure Machine Learning Studio で、**ノートブック**に移動し、上部のメニューで**ファイルのアップロード**オプションを選択します。

3. ローカルコンピューターを参照して、ダウンロードしたノートブック **Model Telemetry.ipynb** を探し、ターゲットフォルダーとして **MCW-MLOps** フォルダーを選択します。次に、**アップロード** を選択します。

4. 上部のバーで、ノートブックの実行に使用する **mlops-compute** コンピューティングインスタンスを選択します。**編集**ドロップダウンを選択し、**Jupyterで編集**を選択します。新しいブラウザウィンドウが開きます。

5. ノートブック内の指示に従って、タスクを完了します。完了すると、デプロイされたモデルの [Application Insights](https://docs.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview) 統合とデータ収集の両方がアクティブ化されます。

6. エラーが発生した場合（たとえば、**サービスへのコンプライアンス分類サービスへの要求が多すぎる（オーバーロードされている）**または**サービスコンプライアンス分類サービスの準備ができたレプリカはありません。**）場合、App Insights を有効にした後でデプロイした Web サービス（**Model Telemetry** ノートブックの最後のセル）では、5 分待ってから、セルを再実行して呼び出しを行う必要があります。

### タスク 2: Application Insights のテレメトリを確認する

1. [Azure portal](https://portal.azure.com) に移動し、このラボ用に作成したリソースグループ（Azure Machine Learningサービスワークスペースが作成されたグループ）を見つけます。

2. リソースグループで Application Insights インスタンスを見つけて選択します。

    ![The Application Insights resource is selected in the resource group.](media/model-telemetry-01.png 'Resource Group Overview')

3. **Overview** に移動します。

4. 右側のセクションの一番上の行から、**ログ**を選択します。空の新しいクエリで Application Insights クエリエディターが開きます。表示されている場合は、**クエリ例**ポップアップを閉じます。

    ![On the Application Insights resource screen, the Overview item is selected in the left menu, and the Logs item is selected from the top toolbar.](media/model-telemetry-02.png 'Application Insights - Dashboard')

5. 左側のペインで、**Tables** タブが選択されていることを確認します。

6. **リクエスト**にカーソルを合わせ、右側のアイコン「このテーブルのサンプルレコードを表示」を選択します。 次に、**実行**を選択します。

    ![On the Application Insights Logs screen, a New Query tab is shown with the Tables tab selected. The icon next to the requests table is selected.](media/model-telemetry-03.png 'Create Requests Query')

7. 表示された結果を見てください。Application Insights は、モデルに対して行われたすべての要求をトレースしています。テレメトリ情報が反映されるまでに数分かかることがあります。結果が表示されない場合は、しばらくお待ちください。モデルを呼び出して 1 分待機し、**実行**を選択してApplication Insights クエリを再実行します。

   ![On the Application Insights Logs screen, a query is run against the requests table and a list of results is displayed.](media/model-telemetry-04.png 'Requests Query Results')

> **Note**: **実行**を選択して Application Insights クエリを再実行した後、テレメトリ情報が表示されない場合。**Model Telemetry** ノートブックの最後のセルをさらに数回再実行して、より多くのデータを生成してください。次に、このページで**実行**を選択して、Application Insights クエリを再実行します。

### タスク 3: 収集したデータを確認する

1. [Azure portal](https://portal.azure.com) に移動し、このラボ用に作成したリソースグループ（Azure Machine Learningサービスワークスペースが作成されたグループ）を見つけます。

2. リソースグループでストレージアカウントインスタンスを見つけて選択します。

    ![The Storage account resource is selected in the resource group.](media/model-telemetry-05.png 'Resource Group Overview')

3. **Storage Explorer (preview)** に移動します。

4. **BLOB CONTAINERS** セクションを展開し、**modeldata** コンテナーを特定します。**modeldata** コンテナが表示されない場合は、**More-> Refresh** を選択します。

    ![In the Storage Explorer screen, the BLOB CONTAINERS item is expanded with the modeldata item selected.](media/model-telemetry-06.png 'Storage Explorer')

5. 収集したデータを含むCSVファイルを特定します。出力 blob へのパスは、次の構造に基づいています。

    **modeldata -> subscriptionid -> resourcegroup -> workspace -> webservice -> model -> version -> identifier -> year -> month -> day -> inputs.csv**

    ![In the Storage Explorer, the modeldata container is selected beneath BLOB containers. The inputs.csv file is selected in the list of files at the path specified above.](media/model-telemetry-07.png 'Storage Explorer - inputs.csv')

## ハンズオンラボの後

所要時間: 5分

予期しない請求を回避するために、ラボの完了時にすべてのラボリソースをクリーンアップすることをお勧めします。.

### タスク 1: ラボのリソースをクリーンアップする

1. Azure Portal に移動し、このラボ用に作成したリソースグループ（Azure Machine Learningサービスワークスペースが作成されたグループ）を見つけます。

2. コマンドバーから **リソースグループの削除** を選択します。

    ![Screenshot of the Delete resource group button.](media/cleanup-01.png 'Delete resource group button')

3. 表示される確認ダイアログで、リソースグループの名前を入力し、**削除**を選択します。

4. リソースグループが正常に削除されたことの確認を待ちます。待たずに、何らかの理由で削除が失敗した場合、予期しないリソースが実行されたままになる可能性があります。アラームアイコンからアクセスできる通知ダイアログを使用して監視できます。

    ![The Notifications dialog box has a message stating that the resource group is being deleted.](media/cleanup-02.png 'Delete Resource Group Notification Dialog')

5. 通知が成功を示したら、クリーンアップは完了です。

    ![The Notifications dialog box has a message stating that the resource group has been deleted.](media/cleanup-03.png 'Delete Resource Group Notification Dialog')

ハンズオンラボに参加した後は、提供されたすべての手順に従ってください。