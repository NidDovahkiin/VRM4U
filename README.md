# VRM4U

[English Doc](https://github.com/ruyo/VRM4U/blob/master/README_en.md)

## はじめに
VRM4UはUE4で動作する、VRMファイルのインポーターです。

**使い方は [こちらのページにあります](https://ruyo.github.io/VRM4U/)**

※配布用のexe作成、モバイル実行には、ソースリポジトリのデータが必要です。 後述の手順を参照ください。


## 特徴
|||
|----|----|
|![2](https://github.com/ruyo/VRM4U/wiki/images/shot/03.png)|![2](https://github.com/ruyo/VRM4U/wiki/images/shot/04.png)|
|![2](https://github.com/ruyo/VRM4U/wiki/images/shot/01.png)|![2](https://github.com/ruyo/VRM4U/wiki/images/shot/02.png)|

 - VRMファイルをインポートできます。
 - アニメーション
     - 骨、Morphtarget・BlendShapeGroup、揺れ骨・コリジョン などが生成されます。
     - 揺れ骨の挙動はVRMSpringBoneかPhysicsAssetを選択できます。
     - Humanoid用のRIGが生成されるので、アニメーションを手軽にリターゲット可能です。
 - マテリアル
     - MToonを再現したマテリアル。影色の指定や、アウトラインの色・太さ調整、MatCapなど一通り適用されます。
     - 既存のPBR背景の中にキャラクタを描画できます。ポストプロセスを利用しません。
 - モバイル
     - BoneMapリダクションを使うことで、公式のUE4エディタからモバイルでSkeletalMeshを利用できます。
     - 描画はForward/Deferred両方に対応しています。

## 動作環境
 - UE4.20〜UE4.27
 - Windows, Android, iOS, Mac(要プロジェクトビルド)
 - UE4.19も動きますが、マテリアルは生成されません。

## 使い方
- **配布用のexeを作成したり、モバイルで実行する場合は、後述のソースリポジトリからダウンロードしてください。**
- エディタでのみ利用する場合は、[releases](https://github.com/ruyo/VRM4U/releases/latest)より利用するバージョンのプラグインをダウンロードし、
   「.uproject」とおなじ場所に「Plugins」フォルダを展開してください。

### サンプルマップ
- VRM4UContent/Maps/VRM4U_sample.umap
- ContentBrowserに表示されない場合は、以下の項目を確認ください。
![3](https://raw.githubusercontent.com/wiki/ruyo/VRM4U/images/samplemap.png)

### 使い方
- VRMファイルをドラッグ＆ドロップしてください

||
|----|
|![2](https://github.com/ruyo/VRM4U/wiki/images/overview.gif)|
|[![](https://img.youtube.com/vi/Qlz0bUSLjss/0.jpg)](https://www.youtube.com/watch?v=Qlz0bUSLjss) https://www.youtube.com/watch?v=Qlz0bUSLjss|


### 仕組み
詳しく知りたい方はこちら


https://speakerdeck.com/ruyo/vrm4u-wakaru

## 作った人
[@ruyo_h](https://twitter.com/ruyo_h)

## ライセンス

|||
|----|----|
|MIT|VRM4U|
|MIT|[RapidJSON](https://github.com/Tencent/rapidjson/)|
|3-clause BSD-License|[assimp](https://github.com/assimp/assimp), [assimp](https://github.com/ruyo/assimp)|

### ソース
UE4アカウントの紐づけが必要です。

ライセンスの都合上、念の為EpicGamesアカウント紐付けにしています。手間ですみません。。

https://github.com/ruyo/UnrealEngine_VRM4UPlugin （404エラーページが出る場合は[こちらより紐付けをしてください](https://www.unrealengine.com/ja/blog/updated-authentication-process-for-connecting-epic-github-accounts)）

https://github.com/ruyo/assimp


公開の体裁を含め 多くの方の情報を参考にさせて頂いています。  
ありがとうございます。

### リリース履歴
- 2022/04/05
    - **注意）インポート済のデータがある場合、VrmAssetListでアセット参照警告が出ることがあります。アセットの再保存で解消されます。**
    - UE5.0 インポート時、IKRetargeter用アセットを自動生成
    - UE5.0 EpicSkeletonからVRMへ、リターゲット用アセットを自動生成
    - 調整パネルより、マテリアルをユーザ指定のものに差し替えできるようにした
- 2022/03/17
    - UE5.0 BVHインポートが動作しないのを修正した
    - UE5.0 IKRigアセットを生成するようにした（VRM, EpicSkeleton両対応）
    - PMXインポートでクラッシュするのを修正した
    - AssetListObjectのカラーを白に寄せた
- 2022/03/08
    - UE5.0 VRM4Uの全機能が動作するようにした。
    - UE5.0 インポート後、エディタ再起動するとMorphが消えるのを修正した
    - UE5.0 MorphRigの保存時に停止するのを修正した
    - UE5.0 PKGでのランタイムロードが停止するのを修正した。
    - Mac インポート時に停止するのを修正した。
    - 古いUniVRMで出力するとアルファマスクが抜けないのを修正した（OpaqueとCutoffの両方指定がある場合Maskとして扱うようにした）
- 2022/02/28
    - UE5.0でControlRigコピースクリプトが動作するよう修正した。（ただUE5.0でのMorphTargetはうまく動作しない）
    - IKRigに不要な腰回転があるのを修正した。
    - ランタイムロードで停止するモデルがあったのを修正した。
    - アルファマスクが抜けないのを修正した（opaque判定が間違っているのを修正）
    - assimpを更新(v5.2.2)
- 2022/02/23
    - **注意）5.0のプラグインをPreview対応版に差し替えました。この先はEA版をサポートしません。必要あれば20220214版をご利用ください。**
    - UE5.0preview版に対応した。
    - 5.0でのインポート時、SSSProfileを初期値で作成するようにした。ノイズが出るため。
    - プラグインの配置場所を自由にできるようになった。
- 2022/02/14
    - **注意）MToonMaterialSystemでのShadeShift調整効果を正負反転し、VRM10の挙動に合わせています。全体補正を利用している場合は従来パラメータの正負を反転ください。未使用であれば影響ありません。**
    - 同名のファイルインポート時、リインポートか強制上書きを選択できるようにした。初期設定ではリインポート。
    - プラグイン側のJSON parserを置き換えた「JSON for Modern C++」-> 「RapidJSON」
    - VRM10: モデル法線が反転していたのを修正した。
    - VRM10: 最新のMToonパラメータに対応した。（Linear色空間の対応、ShadeShiftとToonyの処理変更）
- 2022/02/04
    - リターゲット時、スケールや移動量を調整できるようにした。
    - リターゲットの骨名やリファレンスポーズを指定できるようにした。骨名の対応リスト出力ツールを追加した。
    - Macのビルド設定をStaticLibに切り替えた。
- 2022/01/28
    - グレイマンからのリアルタイムリターゲット機能を追加した [使い方](https://ruyo.github.io/VRM4U/03_gray/)
    - リムテクスチャ、UVスクロールマスクテクスチャに対応した。
    - MToonAttachにて不要なDynamicMaterialが生成されるのを対処した。
    - FKRig関連のActorをリネーム、整頓した。
    - Linuxビルドに対応した。
- 2022/01/20
    - サンプルのモデルがUE4.20～4.25で読めないのを修正した。
    - ue4mannequinにリネームしたSkeletonで、ContorolRigによる視線操作が動かないのを修正した。
    - 新FKRigシステム、サンプルマップを追加した。
    - 開発版UE5の警告を対処した。
- 2022/01/08
    - VMCによる姿勢の回転軸が一部間違っていたのを修正した。
    - VMCのトラッカーを利用したサンプルを追加した。
- 2022/01/05
    - PostToon、MorphRIgがUE5で動作しないのを修正した。一部のファイルをUE4.27で更新していたのを巻き戻した。
    - VMC によるキャラクタ移動を反映した。身長差によるスケール指定できるようにした。（初期値はx1.0）
- 2022/01/04
    - VMC Protocolに対応した。
    - VRM1:インポート時の正規化（ローカル軸の破棄）をオプションで選択可能にした。データ的にはVRM0と同じ状態で読み込める。
- 2021/12/19
    - 骨名が重複したモデルのインポート時に クラッシュしてしまうことがあるのを修正した。
    - PostToonのVRMAssetListを上書きできるようにした。
    - pmxのHumanoid骨リネームに対応した。
    - UE5開発最新ソースでのビルドに対応した
- 2021/11/23
    - Actorの構成によって、MToonAttachActorの位置がずれることがあるのを修正した。
    - マテリアルアニメーションを設定したモデルでクラッシュする場合があるのを修正した。
    - assimpを最新版(2021/11/13版)に更新した
    - VRM1.0βのglTF部分のみ、読み込めるようにした
    - VRMSpringBoneの初期化で骨が暴れるのを抑制した（Tポーズ位置で初期化するようにした）
    - ControlRigに指用のコントローラを追加した。
    - FOV操作用ギズモを、キャラスケールにあわせるようにした。
- 2021/11/19
    - VRMSpringBoneがWindDirectionalSourceの影響を受けられるようにした。風制御Actorの挙動も合わせた。
    - VRMSpringBoneが暴れないよう、衝突時の押し出し処理を変更した。
    - リムライトの計算方法を正確にした。従来カメラ向きを利用していたものを、カメラ位置に変更した。
    - 日本語エディタにて、調整パネルが正しく動作しないのを対応した。
- 2021/11/08
    - SSS ColorScaleのデフォルト値を修正（Alphaを0→1に変更）
- 2021/11/07
    - **注意）MToonLitがシーンによってやや暗くなります。負荷削減のためSkyLightを参照しないようにしました。従来に戻すにはマテリアルよりbUseSkyLightDirectをONにしてください**
    - マテリアルを大幅に最適化した
    - SSSマテリアルを適用する際に、半透明マテリアルをそのまま利用できるようオプションを追加した
    - 調整パラメータ追加した（半透明カラースケール、リムライトカラースケール）
    - リムライトとmatcapについて、法線補正の影響を受けないようにした
    - テクスチャ圧縮フォーマットの初期値をBC7に変更した
- 2021/10/31
    - Unlitマテリアルについて、法線を使う処理が動かなくなっていたのを修正した
    - Raytrace利用時、不要な影が落ちるのを修正した
    - アウトラインカラーを一括設定できるようにした
    - 各種カラー指定について、乗算と上書きを切り替えできるようにした (Alphaが0だと乗算、1だと上書き)
    - ControlRigで腕のIKに肩が連動するようにした
    - UE5.1(開発Stream):ビルドに対応した。MorphリネームオプションをデフォルトOFFにした
- 2021/10/19
    - PostToon機能を追加した。[解説はこちら](https://ruyo.github.io/VRM4U/02_toon/)
    - 白目補正にオプション追加。デカールor半透明を選択できるようにした。
- 2021/10/11
    - 影が描画されないことがあるのを修正した(MaterialSystemがなくても 正常に影が描画できるようにした)
    - ControlRigへのベイク時、肘や膝が大きくズレてしまうことがあるのを修正した。
    - パース操作時のシーケンサー処理負荷を軽減した。GlobalTimeChckerを削除した。
    - 白目補正を嘘パースに対応させた。
- 2021/09/22
    - 嘘パースの初期パラメータを変更した。モデルを破綻しにくくした。
    - 嘘パースのロケータにコリジョンがあったのを削除した。
    - UE5:MorphTargetの文字列チェックを厳密にするモードを追加した。ControlRig対応のため。
- 2021/09/19
    - BlendShapeGroupパラメータをシーケンサー制御できるようにした。
    - リミテッドアニメについて、カメラアタッチモードを追加した。モーション固定時、カメラに追従できるようにした。
    - 嘘パースの機能を拡張した。標準マテリアルに対応したパース補正ノードを追加した。
- 2021/09/04
    - BlendShapeGroupのマテリアルパラメータを適用できるようにした
    - Humanoid骨をリネームした場合も、ControlRigを生成できるようにした
    - MobileHDRが有効な時、Exposure、FilmicTonemapper補正を有効化するようにした
- 2021/08/31
    - UE4.27のビルド時の警告を対処した。
    - ControlRig: 手指の開閉の動作を操作しやすくした。肘の方向を背骨に追従させるようにした。
- 2021/08/20
    - UE4.27に対応した。
    - ポストフィルタを整頓した。ブラーフィルタを追加した。
    - 汎用エフェクトを追加した。
    - VRMSpringBoneを設定するWBPを追加した。
    - 影描画にのみZOffsetを設定できるようにした。
- 2021/08/06
    - ランタイムロードサンプルを整頓した
    - MorphのControlRigをシンプルにした。通し番号を削除した
    - ライトリグのパラメータ変更処理を軽減した
    - SpringBoneのデバッグ表示処理を軽減した
- 2021/07/13
    - ランタイムロードを最適化、非同期読み込みに対応した
    - WBPによるMorphTarget指定について、初期設定では単体モデルのみ操作するようにした
    - SubsurfaceProfileのデフォルトパラメータを変更した（Profile設定）
    - PostShadowによるToon機能を追加
- 2021/07/02
    - モバイル用ランタイムロードの下地を追加した
    - WBPより、BaseColorRateを変更できるようにした
    - SubsurfaceProfileのデフォルトパラメータを変更した。(BaseColorRate 1.0 -> 0.9)
    - CharacterBaseのコリジョンを変更した
- 2021/06/21
    - assimpを更新した(20210616)
    - モデルインポート時のメモリリークを修正した。
    - 法線補正の精度が低いのを対処した。法線にランダムオプションを追加した。
    - UE5: 輪郭線がクリッピングされるのを対処した。
- 2021/06/09
    - ControlRigに補助骨ベースを追加した。ねじり補正を有効化した。
    - ControlRigの膝の動きを修正した。指の操作を追加した。
    - マテリアル調整ウインドウから、SkyLightScaleを制御できるようにした。
    - UE4.27preのビルドに対応した。
    - UE5: 日本語のMorphをWidgetから操作できないのを対処した。（ただキー追加は未対応）
- 2021/06/04
    - FrontFaceCullingのモデルに対応した。
    - UE5: Morph用WidgetBluePrintでActornoサーチに失敗するのを修正した
    - UE5: フェイシャルキャプチャ用のPoseAsset生成に失敗するのを修正した。
    - UE5: トーンマップオプションのうち、利用可能なものを有効化した。
- 2021/05/30
    - マテリアルタイプに SubsurfaceProfileモードを追加した。
    - 法線マップのG反転オプションを有効化した
    - UE5：EditorUtilityWidgetの中で 視認性が悪いものを対処した。Shadow切り替えメニューを追加した。[機能解説はこちら](https://ruyo.github.io/VRM4U/51_ue5/)
    - UE5：Pythonスクリプトのうちエラーになるものを対処した。
- 2021/05/28
    - UE5に対応した。
    - PMXインポート時、IK骨追加すると停止してしまうのを修正した。
    - FBXエクスポート時、骨のリネームが反映されないのを修正した。
- 2021/05/12
    - 調整ウインドウのパラメータ表示を整頓した。項目を追加した。
    - キャラライト設定時、ライトチャンネルを即座に反映するようにした。
    - ControlRigへのベイク時、関節の方向がずれることがあるのを修正した。つま先を追加した。
- 2021/05/04
    - マテリアル調整ウインドウを追加した。[機能解説はこちら](https://ruyo.github.io/VRM4U/01_material/)
    - AttachActorのTargetActor判定を緩めた。カテゴリ名をわかりやすくした。
    - bloom, colorgradationのポストフィルタパラメータを扱いやすくした
- 2021/04/30
    - シーケンサーからキャラのパース固定機能をプレビューできるようにした
    - パース時のDepth補正オプションを追加した。
    - パラメータ、カテゴリを整頓した（AssetUtil, AttachActor）
- 2021/04/13
    - キャラのパース固定機能を追加した。[機能解説はこちら](https://ruyo.github.io/VRM4U/02_pers/)
    - ベースマテリアルを編集するとエラーが出るのを対処した。attributeノードの繋ぎ方を変更した。
- 2021/04/07
    - MaterialAOをデフォルト値を0->1に変更した。（Lit,SSSが従来より やや明るくなる）
    - 白目の明るさを補正するEyeWhiteを追加した。[機能解説はこちら](https://ruyo.github.io/VRM4U/02_shortcut2/)
    - Macでのビルドに対応した。[Macでの使い方はこちら](https://ruyo.github.io/VRM4U/03_mac/)
    - インポートで一時的に利用していたSkeletonクラスを削除した。
- 2021/03/29
    - ControlRigのIKがカクつくことがあるのを対応した
    - BackwardSolveで肘や膝が不安定なのを修正した
    - MorphRig作成時、途中経過を保存できるようにした（保存オプションを追加。クラッシュ対策）
    - MorphRig操作時、Trackを未選択でもキーを打てるようにした（全Trackからサーチするオプション追加）
- 2021/03/24
    - シーケンサーでフェイシャルアニメーションを制御するためのツールを追加した。[解説はこちら](https://ruyo.github.io/VRM4U/07_controlrig_morph/)
- 2021/03/15
    - MatCapによるリムライト表示について、ポリゴンの継ぎ目で強く出てしまうのを修正した。
    - FilmicTonemapperの逆変換について、強度を変更するパラメータを追加した。MToonMaterialSystemより変更。
    - テクスチャをBC7で圧縮するオプションを追加した
    - テクスチャ未設定の場合、白を割り当てるようにした（オプションで従来のgridテクスチャ表示も選択可）
- 2021/03/10
    - uassetファイルのサイズを小さくした。MorphTarget生成時、不要な変形データを保持していたのを削除した。
- 2021/02/24
    - BP_VrmModelActorを利用した際、MorphTargetのカーブも適用されるようにした。
- 2021/02/23
    - パーフェクトシンクを利用するためのアセットを生成するようにした。
    - トラッキングサンプルに上記サンプルを追加した。
    - VRMのBlendShapeClipをPoseアセットに格納した。
- 2021/02/12
    - ControlRig:リターゲットスクリプトを高速化した
    - ControlRig:リターゲット後、モデルによってeyeやchestのコントローラがずれることがあるのを修正
    - ControlRig:LookAtフラグが誤作動することがあるのを修正
    - OculusQuest2のハンドトラッキングを修正（親指のトラッキング、サンプルの修正）
    - assimpを更新した(20210208)
- 2021/01/24
    - ControlRigのBackwardsSolveに対応した。
    - MtoonAttachActorからDirectionalLightComponentを参照できるようにした
    - SSSマテリアルのEmissiveを通常扱いにした（従来はBaseColorに合成するオプションが有効化されていた）
    - SimpleCharacterサンプルを追加した。
- 2021/01/12
    - ControlRigを上手く適用できないモデルに対応した（PMXで骨階層が異なるもの、準標準ボーンを利用しているもの）
    - LightRigからDirectionalLightComponentを参照できるようにした（SunSkyActor対応）
    - LightRigにDirectionalLightのピッチ角による明るさ補正オプションを追加した。
    - 魚眼効果を追加した。嘘パースの制御方法を変更した。
    - MToonMaterialSystemにSSGIの切り替えオプションを追加した
- 2021/01/02
    - ControlRigに指骨や両足のコントローラを追加した。
- 2020/12/30
    - ControlRigをインポートしたモデルに適用できるようにした。サンプルを追加した。
    - PoseRig設定時、つま先の親骨基準位置がずれているのを修正した。
    - Alphaを別テクスチャから参照できるようにした。(UTS2のアセット対応)
    - ノーマルマップのみUV値にスケールを適用できるようにした。
- 2020/12/04
    - UE4.26に対応した。
- 2020/11/25
    - モデルの一部のパーツの座標がずれてしまうことがあるのを修正した。（パーツの原点がワールド原点でないもの）
- 2020/11/18
    - SSSモードのデフォルトマテリアル設定を変更した（MatCapとShadeColor/ShadeHueShiftを有効化）
    - SingleAssetFile無効時も、AssetUtilによるマテリアル変更を可能にした。
    - MatCapに法線補正が影響しないようにした
    - キャラ用フォグシートを追加した。
    - インポートオプションに、スキンのウェイトの骨数制限を追加。(2～8を選択可能)
    - インポートオプションに、Mipmap生成を追加。
- 2020/10/28
    - VRM以外のファイルについて、デフォルトのアウトラインカラーを設定した。
    - SingleUAssetFile未使用時、未使用なリダイレクタが残ってしまうのを修正した。
    - VRM4UEditorモジュールがゲームビルドで失敗することがあるのを修正した。
- 2020/10/09
    - なんでもインポート時、テクスチャファイル名に2バイト文字が入っていると正しくマテリアル作成できないのを修正した。
- 2020/10/08
    - インポート時にSkeletonを指定すると、骨がずれてしまうのを修正した。
    - UE4.26用にAOパラメータを再設定した。
- 2020/09/17
    - UE4.24のランタイムロードで停止するのを修正した。
    - Skeleton指定でインポート失敗した時、停止するのを修正した。
    - エフェクトマテリアル用にUVを操作できるようにした。
- 2020/08/21
    - カメラターゲットが無い時、ズームできなくなるのを修正した。
    - FilmicToneMap無効化をパラメータで制御できるようにした。
    - エフェクトマテリアル作成用の機能を追加した。
    - ランタイムロードするとMorphTargetが動作しないのを修正した。
    - ランタイムロードサンプルにファイル選択ダイアログを追加した。
    - マテリアルサンプルにSSSを追加した。
- 2020/08/07
    - モバイルのmatcapが真っ白になるのを修正した。
    - 注視キャラクタのスケール値をライトやカメラに適用するようにした。
    - PBRマテリアルもMPCで調整できるようにした。
- 2020/07/25
    - インポートマテリアルを整頓した。インポート時にSSSマテリアルを選択できるようにした。
    - キャラカメラのフォーカス位置を変更できるようにした。（F,G,Hキー）
    - キャラカメラにブリージングオプションを追加した。
    - キャラライトの回転軸がずれることがあるのを修正した。
    - AssImpなんでもインポート時、拡張子の判定がすり抜けることがあるのを修正した。
- 2020/07/21
    - ベースマテリアルが正しく描画されないのを修正した（MaterialFunctionにした時のミス）
- 2020/07/18
    - LiveLinkFaceサンプルを整理しました。
- 2020/07/16
    - UE4.25向けのLiveLinkFaceサンプルを追加した。
    - キャラカメラのpitchが動作しないことがあるのを修正した。
    - ベースマテリアルをMaterialFunctionにまとめた。
    - build, cook時に警告が出ている箇所を対処した。
- 2020/07/11
    - （注意）エディタのプラグインウィンドウより明示的にプラグインを有効化してください。
    - BlueprintProjectのパッケージ実行時にエラー終了するのを修正した。
    - リファレンスがA-poseのモデルに対して、T-poseを明示的に作成するようにした。
    - リファレンスポーズを後から変更できるようにした。
    - assimpを最新にマージした。assimpのサポートするモデルフォーマットを読み込み可能にした。
- 2020/06/25
    - マテリアル毎の法線補正機能を追加した。
    - VRの客観視点に、キャラクターカメラの画像を設定できるようにした。
    - カラーグラデーションの初期値を変更し、上部2隅のみ色を残した。
- 2020/06/11
    - キャラクターrigで指が動作しないのを修正した。
    - ランタイムロードでモデルが崩れるのを修正した。
    - 無名のテクスチャのロードに失敗することがあるのを修正した。（最適化済Vroidモデル対策）
    - ModelActorの処理負荷を下げた。
    - PoseCopy時、モデルを差し替え可能にした
- 2020/05/30
    - MaterialUtil処理を高速化した。
    - アニメーションプレビュー処理を高速化した。
    - プリミティブ毎のCastShadowsが効かないのを修正した（要再インポート）
    - ランタイムロードサンプルのアニメーションが動作しないのを修正した。
- 2020/05/20
    - UE4.25でOculusVRプラグインが無効の時、停止してしまうのを修正した。
    - インポート時、UAssetを個別に保存できるようにした。
    - SSS切替時のデフォルトパラメータを調整した。
    - RectLightのアーティファクトが目立たなくなるようにした。（ShadowSlopeBiasを変更した）
- 2020/05/17
    - 汎用的なキャラライトを追加した。初期値をSpotLightに戻した。（SSSでノイズが出るため）
    - SSSパラメータをMaterialSystemで一括オーバーライドできるようにした。
    - キャラカメラに、キャラ注視のまま操作できるモードを追加した。
    - 色が残りやすいBloomを追加した。
    - VRMインポート時のデータチェックを厳密にし、クラッシュしにくくした。
- 2020/05/11
    - 描画クオリティをMaterialSystemから変更できるようにした。
    - SSS設定時のラフネス初期値を変更した(0.8->0.7)
    - SSS設定時のNoTranslucentオプションが動作しないことがあるのを修正した。
    - インポート時のマテリアルマージで半透明が判別できないのを修正した。
    - 4.25でのインポート後、エディタ再起動でブレンドシェイプが消えるのを修正した。
- 2020/05/06
    - UE4.25に対応した。
    - キャラマテリアルにPBRモードを追加した。
    - サブライトを設定できるようにした。
    - マテリアル切り替え時にエディタが停止することがあるのを修正した。
    - マテリアルに彩度調整を追加した。
- 2020/05/02
    - Editor用のモジュールを追加した。
    - rig生成時、NearZを自動で変更(10->1)するようにした。選択しにくい場合の対処のためZオフセットを変更した。
    - rigからAnimSequenceを出力できるようにした。
- 2020/04/29
    - キャラライトを面光源にした。オプションでスポットライト変更。
    - MaterialSystemのPostprocess優先度を上げた。0->10
    - morph操作時、初期向きをモデルに合わせた。
    - 全身rigモードを追加した。
    - rigの表示位置をターゲットモデルに合わせた。
- 2020/04/23
    - rigとlookAt組み合わせ時、PIEで頭位置がズレるのを修正した。
    - マテリアル一括編集ツールを追加した。
    - 小物Attach用のモードを追加した。
- 2020/04/20
    - サンプルを更新・追加した（リグ、カラーグレーディング、トラッキング）
    - rig生成時、半透明選択を有効化した。
    - rigの上体の位置と回転を分離した。
    - 初期ポーズのON/OFFを選択可能にした。（アタッチがずれる対処）
- 2020/04/18
    - 初期ポーズ機能をONにした。
    - ポーズを微調整するRigを追加した。
    - テンプレートモデルVRoidSimpleを最適化した。リターゲットポーズを追加した。
- 2020/04/13
    - 前回の更新で揺れ骨が動作しなくなったのを修正した。(初期ポーズ機能をOFFにした)
    - glb, gltfのインポート時に座標系がずれるのを修正した。
    - インポート時にpbrマテリアル指定していても、mtoonで出力されることがあるのを修正した。
- 2020/04/11
    - アニメーションの初期ポーズを適用できるようにした。
    - BPの命名に沿わないものをリネームした。
    - ポスト処理による4色カラーグレーディングを追加した。
    - Standaloneでアニメーションが動作しないのを修正した。
    - ARKitのフェイシャル、OVRLipsyncのアニメをコピーできるようにした。
- 2020/04/04
    - 透過ウインドウに制限を入れた（新規ウインドウ実行時のみ有効）
    - UE4.25 gameビルドに対応した。
    - MToonMaterialSystemに自前のPostProcessVolumeを持たせるようにした。
    - Exposureをオーバーライドするオプションを追加した。
    - 一部のモジュールをMacで動作できるようにした。（ただしインポートは不可）
- 2020/03/31
    - 色再現を優先するモードを追加した（FilmicToneMapperをOFF、色逆変換を無効化）
    - デバッグカメラ操作に、Roll回転とZoomを追加した。
    - 揺れ骨簡易設定のデフォルトパラメータを変更した。
    - AnimBlueprintにトラッキング用IKを追加した。UE4.25用にOculusQuestのハンドトラッキングテストを追加した。
- 2020/03/25
    - 揺れ骨を簡易的に再設定できるようにした。デバッグ表示を追加した。
    - リターゲットポーズを追加した。足の開閉パターン2種類ぶん。
    - ライセンス情報が欠けていたのを修正した。
    - インポートウインドウにモデルのライセンスと画像サムネイルを表示するようにした。
- 2020/03/21
    - ポーズコピー元にSkeletalmeshを指定できるようにした。morphを連動させた。
    - ウェイトが無いパーツについて、追従する骨を正しく設定するようにした。
    - ランタイムリターゲット時、RootMotionが反映されないのを修正した。
    - 背景のクロマキー、ウィンドウ透過サンプルを追加した。
- 2020/03/17
    - 風のゆらぎ、座標によるディレイを追加した。
    - 揺れ骨のカテゴリ変更、風を無視する骨を設定できるようにした。
    - ポーズコピー時、フレームレート操作できるようにした。
    - ドキュメントのサンプルBVHを読めるようにした。
- 2020/03/15
    - 多くの機能をAnimControlComponentにうつした。
    - 風を設定できるようにした。
    - 揺れ骨の設定をActorから操作できるようにした。
    - アニメーションのフレームレートを操作できるようにした。
    - Stencil設定用に、モデルを姿勢ごとコピーするActorを追加した。
- 2020/03/12
    - Toonの初期化をConstructionScriptに移動した。
    - UpperChestが無いモデルの視線追従が弱いのを修正した。
    - CustomAnimSequenceのアセット選択候補をリターゲット元のみにした。
    - Morphコントロールをレベル上で確認可能にした。
    - レベル上でアタッチ可能なアクタ VRMModelActorを追加した。
- 2020/03/08
    - 視線追従Actorのターゲットを修正した。
    - PIEでキャラライトを設定すると 座標がずれるのを修正した。
    - UE4.25pre1に対応した。
- 2020/03/04
    - Skeletonのマージをした後、VRMSpringBoneで停止することがあるのを修正した。
- これ以前のものはこちら → https://github.com/ruyo/VRM4U/blob/master/CHANGELOG.md

