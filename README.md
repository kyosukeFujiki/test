パスワードを聞かれますので、 ***`docker_password`*** と入力してください。  

> [!WARNING]
> aaa
> bbb

`likes`テーブルは、下記を追加します。
* `id`
* いいねをしたユーザーの`email`
* 年表の`id`
* `members`
* `histories`

さらに、`members`と`histories`テーブルには、`likes`を追加します。  
上記のようにすることで、`members`と`histories`テーブルから、`likes`を取得できるようになります。

```go
...

model members {
  ...
  likes likes[] // likesカラムをmembersテーブルに追加
}

model histories {
  ...
  likes likes[] // likesカラムをhistoriesテーブルに追加
}

model pvs {
  ...
}

model tags {
  ...
}

// ↓↓↓↓↓↓↓↓↓↓↓↓↓↓ 一番最後の行に、likesテーブルを追加する ↓↓↓↓↓↓↓↓↓↓↓↓↓↓
model likes {
  id        Int   @id @default(autoincrement())                             //いいねID
  member_email String                                                       // 投稿者E-Mail
  members   members? @relation(fields: [member_email], references: [email]) // membersテーブルと紐付け
  history_id String                                                         // 年表ID
  histories   histories? @relation(fields: [history_id], references: [id])  // historiesテーブルと紐付け
}
```


```stl
solid cube_corner
  facet normal 0.0 -1.0 0.0
    outer loop
      vertex 0.0 0.0 0.0
      vertex 1.0 0.0 0.0
      vertex 0.0 0.0 1.0
    endloop
  endfacet
  facet normal 0.0 0.0 -1.0
    outer loop
      vertex 0.0 0.0 0.0
      vertex 0.0 1.0 0.0
      vertex 1.0 0.0 0.0
    endloop
  endfacet
  facet normal -1.0 0.0 0.0
    outer loop
      vertex 0.0 0.0 0.0
      vertex 0.0 0.0 1.0
      vertex 0.0 1.0 0.0
    endloop
  endfacet
  facet normal 0.577 0.577 0.577
    outer loop
      vertex 1.0 0.0 0.0
      vertex 0.0 1.0 0.0
      vertex 0.0 0.0 1.0
    endloop
  endfacet
endsolid
```
```topojson
{
  "type": "Topology",
  "transform": {
    "scale": [0.0005000500050005, 0.00010001000100010001],
    "translate": [100, 0]
  },
  "objects": {
    "example": {
      "type": "GeometryCollection",
      "geometries": [
        {
          "type": "Point",
          "properties": {"prop0": "value0"},
          "coordinates": [4000, 5000]
        },
        {
          "type": "LineString",
          "properties": {"prop0": "value0", "prop1": 0},
          "arcs": [0]
        },
        {
          "type": "Polygon",
          "properties": {"prop0": "value0",
            "prop1": {"this": "that"}
          },
          "arcs": [[1]]
        }
      ]
    }
  },
  "arcs": [[[4000, 0], [1999, 9999], [2000, -9999], [2000, 9999]],[[0, 0], [0, 9999], [2000, 0], [0, -9999], [-2000, 0]]]
}
```
## ボタンコンポーネントの作成

次にボタンコンポーネントを追加していきます。  
\*\*行目にある return を編集していきます。

div タグ・Button タグ・Image タグを下記のように編集してください
60行目らへん

#### ***./app/src/pages/detail/[id].page.tsx***
```tsx
return (
  <>
    <HeadTitle title={myHistory.title} />
    <HeadSns title={myHistory.title} url={shareUrl} />
    <Header />
    <Container css={container}>
      <h1 css={title}>{myHistory.title}</h1>
      <MyHistoryChart myEvents={myHistory.events} width="90%" isReadonly={true} />
      <div css={historyDataText}>{`作者: ${myHistory.author} (JST: ${updatedJst} 更新)`}</div>
      {/* ################## ここから ################# */}
      <div>
        <Button colorScheme="gray" variant="outline">
          <Image src={heartNotActive} alt="" height={20} />0 いいね
        </Button>
      </div>
      {/* ################# ここまで ################# */}
    </Container>
    <Footer />
  </>
);
```

## ボタンコンポーネントの作成

次にボタンコンポーネントを追加していきます。  
\*\*行目にある return を編集していきます。

div タグ・Button タグ・Image タグを下記のように編集してください

```tsx
ーーーーーーーーーーーーー /app/src/pages/detail/[id].page.tsx ーーーーーーーーーーーーー
return (
  <>
    <HeadTitle title={myHistory.title} />
    <HeadSns title={myHistory.title} url={shareUrl} />
    <Header />
    <Container css={container}>
      <h1 css={title}>{myHistory.title}</h1>
      <MyHistoryChart myEvents={myHistory.events} width="90%" isReadonly={true} />
      <div css={historyDataText}>{`作者: ${myHistory.author} (JST: ${updatedJst} 更新)`}</div>
      {/* ここから */}
      <div>
        <Button colorScheme="gray" variant="outline">
          <Image src={heartNotActive} alt="" height={20} />0 いいね
        </Button>
      </div>
      {/* ここまで */}
    </Container>
    <Footer />
  </>
);
```

`terminal`
```
git checkout main
```
```
git checkout main
```
```
$ git checkout main
```

```
ーーーーーー ./app/.env.local ーーーーーー
NEXTAUTH_URL="http://localhost:3000"
NEXTAUTH_SECRET=""
GOOGLE_CLIENT_ID=""
GOOGLE_CLIENT_SECRET=""

# minio
ENDPOINT_URL=http://s3:9000
ACCESS_KEY_ID=root
SECRET_ACCESS_KEY=password
REGION=ap-northeast-1
S3_BUCKET_NAME=minio-backet
```

```
ーーーーーー ./app/.env.local ーーーーーー
NEXTAUTH_URL="http://localhost:3000"
NEXTAUTH_SECRET=""
GOOGLE_CLIENT_ID=""
GOOGLE_CLIENT_SECRET=""

# minio
ENDPOINT_URL=http://s3:9000
ACCESS_KEY_ID=root
SECRET_ACCESS_KEY=password
REGION=ap-northeast-1
S3_BUCKET_NAME=minio-backet
```





# 2-環境構築

## 環境構築

まずは環境構築をします。
実際に手元の環境で、マイナビクロニクルを動かしてみたいと思います。

まずは、マイナビクロニクルのリポジトリがあるか確認します。
以下のコマンドで、マイナビクロニクルのリポジトリに移動してください。
（〇〇には自分のチーム番号が入ります）

`terminal`
```
cd ~/mynavi-chronicle-2023-team〇〇
pwd .
→ home/ubuntu/mynavi-chronicle-2023-team〇〇
```

<br>

その後、環境変数を設定するために、`.env.local`ファイルを作成します。

`terminal`
```
touch app/.env.local
```

<br>

上記のコマンドを実行後、`.env.local`ファイルに値を設定します。

`./app/.env.local`
```
NEXTAUTH_URL="http://localhost:3000"
NEXTAUTH_SECRET=""
GOOGLE_CLIENT_ID=""
GOOGLE_CLIENT_SECRET=""

# minio
ENDPOINT_URL=http://s3:9000
ACCESS_KEY_ID=root
SECRET_ACCESS_KEY=password
REGION=ap-northeast-1
S3_BUCKET_NAME=minio-backet
```

`NEXTAUTH_SECRET`に値が設定されておりませんので、以下のコマンドの実行結果を、`NEXTAUTH_SECRET`のダブルクォーテーションの中に入れてください。

`terminal`
```
openssl rand -base64 32
```

<br>

次にポートフォワーディングの設定を行います。
ポートフォワーディングを説明すると長くなってしまうので、ここでは「自分のパソコンと`AWS EC2`上のパソコンをつなげるために必要な番号」と思ってください。

<br>

`VSCode`の`TERMINAL`の横に`PORTS`というタブが表示されていると思いますので、こちらをクリックします。

![portの設定](images/setup-port-before.png)

これでポートの設定は完了です。

![portの設定](images/setup-port-after.png)

<br>

最後にマイナビクロニクルの環境を、ローカルに立ち上げます。

`terminal`
```
docker compose up
```

実際に`http://localhost:3000`に移動し、マイナビクロニクルの画面が表示されているか、確認してみてください。

![](images/setup-top.png)

<br><br><br><br><br><br>

## 作業ブランチの作成

次に、現在自分がいるブランチの名前を表示しましょう。
作業中のブランチ名がわかり、間違えて変更をプッシュしてしまう可能性を少なくすることができます。
以下の画像のような見た目になるように設定します。

![](images/git-branch.png)

<br>

シェルの設定を変更するため、以下の二つのコマンドを実行します。

`terminal`
```
echo "GIT_PS1_SHOWDIRTYSTATE=true" >> ~/.bashrc
echo "export PS1='\[\033[32m\]\u@\h\[\033[00m\]:\[\033[34m\]\w\[\033[31m\]\$(__git_ps1)\[\033[00m\]\n\\\$ '" >> ~/.bashrc
```

最後に以下のコマンドを入力すると、先ほどの画像のようなシェルが表示されます。

`terminal`
```
source ~/.bashrc
```

<br>

次に、自分が作業するためのブランチを作成しましょう。

まず初めに、自分がどのブランチにいるのか（表示されていますが）コマンドで確かめましょう。
確かめるコマンドは、以下のコマンドです。

`terminal`
```
git branch
```

![](images/git-branch-main.png)

<br>

main ブランチにいない方は一度 main ブランチに戻ってきましょう。
戻ってくるコマンドは下記です。これを実行するとブランチ名が main に切り替わると思います。

`terminal`
```
git checkout main
```
```
=== terminal ========
git checkout main
```

<br>

また、main が最新の状態でブランチを切る方が良いので、一度 remote（Github のブランチ） から main ブランチの更新をします。コマンドは下記です。

`terminal`
```
git pull
```

<br>

今回は、上記コマンドを 2 回実行し、2 回目で 「**Already up to date**」 と表示されるのを確認しましょう。

次に、ブランチの作成を行います。
以下のコマンドでブランチの作成と、該当ブランチへの移動ができます。

`terminal`
```
git checkout -b GitHubユーザ名/add-like
```

<br>

（GitHub ユーザ名/add-like の部分は、好きなブランチ名でも大丈夫です。今回は誰が作業したか分かりやすいように GitHub のユーザ名をつけています）

上記実行後、以下のように括弧内がこのようなブランチ名になると思います。
（ブランチ名は GitHub ユーザが SosukeMikami だった場合です）

![](images/git-branch-addlike.png)

実際に作業するブランチに移動できたので、次のセクションに進み、コード実装をしていきましょう。

<br><br><br><br><br><br>

## 下準備 ユーザー情報作成

ハンズオンを行うにあたって、テスト用のユーザー情報を作成します。

[サインイン画面](http://localhost:3000/auth/signin)に遷移して下記の情報を入力してサインインします。

メールアドレス: example@example.com  
ユーザー名　　: example  
パスワード　　: example

![](images/login-login.png)

<br>

サインイン後、[マイページ](http://localhost:3000/mypage) に遷移し、下記画像のようにユーザーが登録されていることを確認します。

![](images/login-mypage.png)





