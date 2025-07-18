### Google AI Studioで「誰でも」業務ツールを開発！〜議事録自動化システムを例に〜

#### 1. はじめに：AI活用への一歩を踏み出せないでいませんか？（1分）

皆さん、AIで「こんなことができたらいいな」と思うことはたくさんあるのに、「チャットでちょっと試しただけで終わってしまっている」あるいは「興味はあるけれど、何から始めればいいかわからない」と感じていませんか？。ご安心ください。今回は、**AIの力を借りることで、従来エンジニアに依頼しなければ実現できなかったことが、誰でも簡単に形にできる時代になった**ことをご紹介します。

本日は、**身近な題材**である「Google Meetの録画と文字起こし機能を活用した議事録の自動生成・編集システム」の開発事例を通じて、AIを活用した開発の基本的な流れを体験していただきます。このプロジェクトは、AI活用で議事録の精度を向上させ、会議後の作業効率を大きく改善できるため、具体的な活用方法や開発の進め方を実践的に学べます。

#### 2. 現状の課題：会議の議事録作成、こんな悩みがありませんか？（1.5分）

皆さんの会社ではGoogle Meetを利用していますか？ Google Meetには「録音」「文字起こし」「議事録作成（Gemini活用）」といった便利な機能が備わっています。しかし、これらの機能を活用して議事録を作成する中で、以下のような課題に直面していないでしょうか？

*   **1. 議事録の元となる情報の正確性に関する課題**: Google Meetの文字起こし機能は日本語にも対応していますが、その精度がまだ不十分で、発言内容が正確にテキスト化されないことがあります。そのため、議事録の信頼性が低く、手動での確認や修正に手間がかかっています。
*   **2. 議事録の構造と活用に関する課題**: 生成された議事録が単なる会話の記録、つまり「テキストの羅列」に留まっていることがあります。社内の公式な記録として活用するために必要な「会議での決定事項」や「次に取るべきアクションプラン（ToDo）」が明確に整理されていないため、会議の結果が分かりにくいという問題があります。
*   **3. アクションプランの進捗管理に関する課題**: 定例会議などで、前回の会議で決定したアクションプランの進捗を確認する仕組みがなく、「完了したのか」「継続中なのか」を追跡・管理できていないリスクがあります。

これらの課題により、議事録の作成と活用に多大な工数がかかっているのが現状です。

#### 3. 解決策：Google AI Studioで「AI議事録作成・活用システム」を開発！（2分）

私たちは、これらの課題を解決するために、Google AI Studioの技術を活用した「AI議事録作成・活用システム」を開発しました。このシステムの目的は、**「正確で、構造化され、次のアクションに繋がる」**議事録の作成・活用プロセスを自動化・効率化することです。

具体的には、以下のような機能をAIとGoogle AI Studioで実現しました。

*   **高精度文字起こし機能**: Google Meetの録画データをインプットとし、Google Cloud Speech-to-Text APIを用いて高精度な文字起こしテキストを生成します。話者の識別も可能な範囲で行います。
*   **議事録の自動構造化機能**: 生成された文字起こしテキストをGoogleのAI「Gemini API」が解析し、「会議の要約」「決定事項」「アクションプラン（担当者、期限含む）」を自動で抽出し、整理された形式で出力します。これが本システムの核となるAI機能です。
*   **手動編集インターフェース**: AIが生成した構造化議事録に対し、ユーザーが手動で内容の修正や追記を行えるシンプルな編集画面を提供します。
*   **アクションプラン管理機能**: 抽出されたアクションプランをリスト化し、「未着手/進行中/完了」のステータスを管理できます。過去の会議のアクションプランも一覧で確認可能です。
*   **エクスポート機能**: 生成・編集した議事録をテキスト形式やMarkdown形式で簡単に出力できます。

これらの機能は、まさに先ほど挙げた議事録作成の課題を直接的に解決します。

#### 4. 「誰でも」開発できた理由：Google AI Studioとアジャイルな開発プロセス（3分）

「でも、AIツールを開発するなんて難しそう…」と感じた方もいるかもしれません。しかし、このプロジェクトは、**エンジニアでなくても業務ツールを開発できる**ことを証明しています。その鍵は、Google AI Studioと私たちが採用した開発アプローチにあります。

*   **Google AI Studioの活用と開発の進め方**:
    *   このシステムは、**要件の整理から始めて、約60分ほどでアプリの開発・Google Cloudへのデプロイ・運用開始までを完了できます**。
    *   開発は「現状サービスの把握」「課題（要件）のヒアリング」「調査・リサーチ」「要件の整理」「設計」「実装」「テスト」「運用」というステップで進められましたが、PoC（概念実証）の段階では設計フェーズを簡略化しました。
    *   特に重要だったのは、**「議事録の自動構造化」機能のプロトタイピングから始める**ことでした。Google AI Studioのプレイグラウンド上で、「このテキストから要約、決定事項、アクションプランを抽出してください」といった簡単な指示（プロンプト）を試行錯誤するだけで、プロジェクトの核となるAI技術が実現可能であることを検証できたのです。
*   **AIが開発プロセスを支援した例**:
    *   開発中にMarkdown形式での出力機能が初期には含まれていなかった際も、機能追加を依頼したところ、**すぐに再実装され、迅速に改善を進めることができました**。
    *   さらに驚くべきことに、テスト用の議事録データやサンプル文書は、**Geminiを用いて自動生成**しました。
    *   実装後も、**AIを使って詳細設計書をリバース生成し、コードとの整合性チェックまでAIに依頼**しました。

このように、Google AI StudioとAIのサポートにより、開発プロセス自体が非常に効率的かつ「誰でも」取り組みやすいものになりました。

#### 5. まとめと今後の可能性：AIであなたの業務をもっと効率的に！（1.5分）

この取り組みの最大の意義は、**従来であればエンジニアに依頼しなければ実現できなかったことが、AIの力を借りることで、誰でも簡単に形にできる時代になった**ことです。

実際に動作するプロダクトは、[提供されているデモリンク](https://poc-meeting-studio-253179510304.us-west1.run.app/)からアクセスできますし、GitHubリポジトリも公開されています。

AIを活用することで、議事録の精度を向上させ、会議後の作業効率を大きく改善できます。私たちは、このプロジェクトを通じて、会議を中心とした業務プロセス全体の生産性向上を目指しています。

あなたの身近な業務課題も、Google AI Studioを使えば、もしかしたら驚くほど簡単に解決できるかもしれません。ぜひ、今日ご紹介した事例を参考に、AIを活用した業務改善に挑戦してみてください。

#### 6. 質疑応答（1分）

---