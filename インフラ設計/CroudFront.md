## 概要
マシマシサーチの画面用CloudFrontの設計を記載する。


## 基本情報
画面名|リソース名|ルートファイル|参照S3|  
--|--|--|--|  
マシマシサーチ|mashi-mashi-dev-cloudfront-001|index.html|mashi-mashi-dev-s3-001|  

## リソース詳細情報

### マシマシサーチ
**mashi-mashi-dev-cloudfront-001**  
- Tag
  - Type: `CloudFront`
  - Name: `mashi-mashi-dev-cloudfront-001`
  - ServiceName: `MashiMashiSearchClient`
  - Usage: `mashi mashi serach client for users`
- レスポンスページPath: `index.html`

**mashi-mashi-dev-s3-001**  
- Tag
  - Type: `S3`
  - Name: `mashi-mashi-dev-s3-001`
  - ServiceName: `MashiMashiSearchClient`
  - Usage: `mashi mashi serach client s3 for users `

## WAF設定

[WAF設定]()参照

## デプロイに使用するアプリケーション
vue CLIを使用する  
以下にインストールするコマンドを記載する  
```bash
npm install -g @vue/cli
# インストール確認

vue --version
```

### vue CLIでのプロジェクト設定

以下のコマンドを実行する。  
一つ下のフォルダに作成されるため、親フォルダに移動する。  

```bash
vue create mashi_mashi_client
```

以下を設定する。  
```bash
Vue CLI v5.0.8
? Please pick a preset: Manually select features
? Check the features needed for your project: Babel, TS, Router, Vuex, Linter
? Choose a version of Vue.js that you want to start the project with 3.x
? Use class-style component syntax? No
? Use Babel alongside TypeScript (required for modern mode, auto-detected polyfills, transpiling JSX)? Yes
? Use history mode for router? (Requires proper server setup for index fallback in production) Yes
? Pick a linter / formatter config: Airbnb
? Pick additional lint features: Lint on save, Lint and fix on commit
? Where do you prefer placing config for Babel, ESLint, etc.? In dedicated config files
? Save this as a preset for future projects? Yes
? Save preset as: vue-setting-mashimashi
```