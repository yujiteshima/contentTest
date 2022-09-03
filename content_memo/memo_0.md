# code block にファイル名を表示する
コードブロックにファイル名を表示したい。
remarkで変換後に自作のプラグインを使って表示することにする。
すでに存在するプラグインを探したが見つけられなかった。
その為にunifiedのエコシステムを理解するところから始めなければならない。

## unifiedとは
remarkはunifiedというもっと大きな枠組みの中のMarkdownを扱うさいに使うものである。
unifiedはテキストと構文木やASTとASTを変化するためのJavaScriprt製フレームワークのことである。
### unifiedにおける用語
#### 構文木
　自然言語を名詞や動詞など、構文に剃って解析して木構造としたものである。
#### AST
　日本語では抽象構文木と言う。　Abstract Syntax Treeの頭文字をとってAST。
　構文木から、文法のための記号や助詞など、意味のない部分を除いた木構造を指す。
　実例としては、HTMKに対するDOMが分かりやすい。```< >```などタグを表す文字はDOMでは保持されない。
#### unisit
　universal syntax tree のことである。
　https://github.com/syntax-tree/unist
　に定義や操作するためのライブラリーがまとまっている。
　unifiedの世界ではASTのベースとなるもの。オブジェクト指向的に言うと全てのASTの親となるもの。
　そのため、基本的にASTを操作するときはunistとして扱うと便利である。
#### parser
　parserはテキストを解釈して、そのparserが解釈できる文法に沿ったASTを生成するもの。
#### compiler
　compilerはparserの反対の動作をする。ASTから文法に沿ってテキストを生成する。
#### transformaer
　transformaerはAST間の変換をするもの
#### vfile
virtualize fileの略で、ファイルを仮想化して扱えるようにしたもの。unifiedではvfileを用いてデータをやり取りする。

### unifiedで対応している文法
unifiedで扱うことのできる文法を列挙する。

#### markdown
Markdown文法の担当としてremarkがある。
remarkにおけるparserはremark-parse, compilerはremark-stringifyである。
transformerは色々ある
remark-rehype : markdown ast -> HTML ast
remark-retext : markdown ast -> 自然言語の構文木
remark-react  : markdown ast -> reactElement

remark の内部処理はmicromarkmarkに移譲されている。
markdownを表すastはmarkdwon ast からmdastと呼ばれている。
操作用のライブラリも用意されている。

#### HTML
HTMLを担当しているのはrehypeである。
rehype-parse, rehype-stringifyがそれぞれparserとcompilerである。
HTML文法におけるASTはhastと呼ばれている。 html astの略。
操作用のライブラリはhastである。

#### 自然言語
retextが担当している。
現在は英語、オランダ語、ラテン文字の自然言語に対応しているようである。絵文字も使える。

#### プラグイン
unifiedはプラグインシステムを採用している。parserやcompilerもプラグインとして提供されており、
transformarは自分で好きなように定義して使うことができる。
