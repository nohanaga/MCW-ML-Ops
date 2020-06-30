![Microsoft Cloud Workshops](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png "Microsoft Cloud Workshops")

<div class="MCWHeader1">
MLOps
</div>

<div class="MCWHeader2">
ハンズオンラボセットアップガイドの前に
</div>

<div class="MCWHeader3">
2020年6月
</div>

このドキュメントに記載されている情報 (URL や他のインターネット Web サイト参照を含む) は、将来予告なしに変更することがあります。別途記載されていない場合、このソフトウェアおよび関連するドキュメントで使用している会社、組織、製品、ドメイン名、電子メール アドレス、ロゴ、人物、場所、出来事などの名称は架空のものです。実在する商品名、団体名、個人名などとは一切関係ありません。お客様ご自身の責任において、適用されるすべての著作権関連法規に従ったご使用をお願いいたします。著作権法による制限に関係なく、マイクロソフトの書面による許可なしに、このドキュメントの一部または全部を複製したり、検索システムに保存または登録したり、別の形式に変換したりすることは、手段、目的を問わず禁じられています。ここでいう手段とは、複写や記録など、電子的、または物理的なすべての手段を含みます。

マイクロソフトは、このドキュメントに記載されている内容に関し、特許、特許申請、商標、著作権、またはその他の無体財産権を有する場合があります。別途マイクロソフトのライセンス契約上に明示の規定のない限り、このドキュメントはこれらの特許、商標、著作権、またはその他の知的財産権に関する権利をお客様に許諾するものではありません。

製造元名、製品名、URL は、情報提供のみを目的としており、これらの製造元またはマイクロソフトのテクノロジを搭載した製品の使用について、マイクロソフトは、明示的、黙示的、または法令によるいかなる表明も保証もいたしません。製造元または製品に対する言及は、マイクロソフトが当該製造元または製品を推奨していることを示唆するものではありません。掲載されているリンクは、外部サイトへのものである場合があります。これらのサイトはマイクロソフトの管理下にあるものではなく、リンク先のサイトのコンテンツ、リンク先のサイトに含まれているリンク、または当該サイトの変更や更新について、マイクロソフトは一切責任を負いません。リンク先のサイトから受信した Web キャストまたはその他の形式での通信について、マイクロソフトは責任を負いません。マイクロソフトは受講者の便宜を図る目的でのみ、これらのリンクを提供します。また、リンクの掲載は、マイクロソフトが当該サイトまたは当該サイトに掲載されている製品を推奨していることを示唆するものではありません。

© 2020 Microsoft Corporation. All rights reserved.

Microsoft および <https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx> (英語) に掲載されているその他の商標は、マイクロソフト グループ各社の商標です。その他すべての商標は、その所有者に帰属します。

**コンテンツ**

<!-- TOC -->

- [MLOps ハンズオンラボセットアップガイドの前に](#MLOps-ハンズオンラボセットアップガイドの前に)
  - [必要条件](#必要条件)
  - [ハンズオンラボの前に](#ハンズオンラボの前に)
    - [タスク 1: Azure Machine Learning ワークスペースを作成する](#タスク-1-Azure-Machine-Learning-ワークスペースを作成する)

<!-- /TOC -->

# MLOps ハンズオンラボセットアップガイドの前に

## 必要条件

1. Azureサブスクリプション。クイックスタートを完了するには、有効でアクティブな Azure アカウントが必要です。お持ちでない場合は、[無料トライアル](https://azure.microsoft.com/en-us/free/)にサインアップできます。

   - Microsoft Azure サブスクリプションは、従量制または MSDN である必要があります。

   - 試用版サブスクリプションは機能しません。Azure リソースクォータの制限に関する問題が発生します。

   - アクセスが 1 つのリソースグループに制限されているサブスクリプションは機能しません。複数のリソースグループをデプロイする機能が必要になります。

2. Azure DevOps サブスクリプション。クイックスタートを完了するには、有効でアクティブな Azure DevOps アカウントが必要です。アカウントがない場合は、[無料アカウント](https://azure.microsoft.com/en-us/services/devops/)にサインアップできます。

   > **Note**: DevOps アカウントでプロジェクトを作成するには、権限が必要です。また、原則でサービスプリンシパルを作成する権限も必要です。**ユーザーがサブスクリプションに対して「所有者」または「ユーザーアクセス管理者」権限を持っていることを確認します**。

3. Azure Machine Learning サービスのワークスペース。 Azure Machine Learning ワークスペースは、機械学習モデルの実験、トレーニング、デプロイに使用するクラウドの基本的なリソースです。Azure サブスクリプションとリソースグループを、サービス内で簡単に使用できるオブジェクトに結び付けます。

4. Azure Machine Learning コンピューティングインスタンス。コンピューティングインスタンスは、ハンズオンラボの演習1で作成したものです。このコンピューティングインスタンスは、ワークスペースのファイル共有にアップロードされたクイックスタート統合ノートブックを実行するためのクラウド上の完全に構成・管理された開発環境として使用されます。

## ハンズオンラボの前に

### タスク 1: Azure Machine Learning ワークスペースを作成する

1. Azure サブスクリプションの資格情報を使用して、[Azure ポータル](https://portal.azure.com)にサインインします。

2. Azure ポータルの左上隅で、**+リソースの作成**を選択します。

3. 検索バーを使用して、**Machine Learning**を見つけます。

4. **Machine Learning** を選択します。

5. **Machine Learning** ペインで、**作成**を選択して開始します。

   ![The Machine Learning page displays with the Create button selected.](media/bhol-01.png 'Open Create Azure Machine Learning Workspace')

6. 次の情報を入力して、新しいワークスペースを構成します。

   - **ワークスペース名**: ワークスペースを識別する一意の名前を入力します。この例では、**quick-start-ws** を使用しています。名前は、リソースグループ全体で一意である必要があります。他の人が作成したワークスペースと区別しやすく、わかりやすい名前を使用してください。

   - **サブスクリプション**: 使用する Azure サブスクリプションを選択します。

   - **リソースグループ**: サブスクリプションの既存のリソースグループを使用するか、名前を入力して新しいリソースグループを作成します。リソースグループは、Azure ソリューションの関連リソースを保持します。この例では、**MCW-MLOps** を使用しています。

   - **ロケーション**: ユーザーに最も近い場所とデータリソースを選択して、ワークスペースを作成します。

   - **ワークスペースエディション**: **Basic**. ワークスペースの種類（ベーシックとエンタープライズ）によって、アクセスできる機能と価格が決まります。 このチュートリアルの演習は、Basic または Enterprise エディションで機能します。

   ![The Machine Learning Create form is displayed populated with the aforementioned values. The Review + Create button is highlighted.](media/bhol-02.png 'Create Azure Machine Learning Workspace page')

7. ワークスペースの構成が完了したら、**レビュー+作成**を選択します。入力したフィールドを確認したら、**作成**を選択します。

    > **Note**: クラウドにワークスペースを作成するには、数分かかる場合があります。

    プロセスが完了すると、展開成功のメッセージが表示されます。

8. 新しいワークスペースを表示するには、 **リソースに移動** を選択します。

9. [Azure Machine Learning Studio](https://ml.azure.com) に移動し、作成したワークスペースを選択するか、Azure Machine Learning ワークスペースの **Overview** セクションの **Try the new Azure Machine Learning studio** で **今すぐ起動** を選択します。

   ![The Machine Learning resource page is shown with Overview selected from the left menu, and the Launch now button highlighted in the Overview screen.](media/bhol-03.png 'Launch the Azure Machine Learning studio')
