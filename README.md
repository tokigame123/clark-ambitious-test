
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CLARK Ambitious Test - 診断スタート</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary-blue: #0066cc;
            --dark-blue: #003d99;
            --light-blue: #e6f2ff;
            --accent-blue: #0099ff;
            --text-dark: #1a1a1a;
            --text-light: #666666;
            --border-radius: 16px;
            --spacing-sm: 8px;
            --spacing-md: 16px;
            --spacing-lg: 24px;
            --spacing-xl: 32px;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Noto Sans JP', sans-serif;
            background: linear-gradient(135deg, #0066cc 0%, #0099ff 100%);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: var(--spacing-md);
        }

        .container {
            width: 100%;
            max-width: 600px;
            background: white;
            border-radius: var(--border-radius);
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
            overflow: hidden;
            display: flex;
            flex-direction: column;
            max-height: 90vh;
        }

        /* ===== ヘッダー ===== */
        .header {
            background: linear-gradient(135deg, #0066cc 0%, #0099ff 100%);
            padding: var(--spacing-lg) var(--spacing-xl);
            display: flex;
            align-items: center;
            justify-content: space-between;
            color: white;
            flex-shrink: 0;
        }

        .header-left {
            display: flex;
            align-items: center;
            gap: var(--spacing-md);
        }

        .header-tag {
            font-size: 28px;
            font-weight: bold;
            letter-spacing: 2px;
            font-style: italic;
            line-height: 1;
        }

        .header-right {
            text-align: right;
        }

        .header-title {
            font-size: 14px;
            font-weight: bold;
            line-height: 1.4;
            letter-spacing: 0.5px;
        }

        .header-subtitle {
            font-size: 12px;
            opacity: 0.95;
            margin-top: 2px;
        }

        /* ===== コンテンツエリア ===== */
        .content-wrapper {
            flex: 1;
            overflow-y: auto;
            display: flex;
            align-items: flex-start;
            justify-content: center;
            padding: var(--spacing-xl) var(--spacing-lg);
        }

        .content {
            width: 100%;
            display: none;
        }

        .content.active {
            display: block;
            animation: fadeIn 0.3s ease-in;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(10px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* ===== ホーム画面 ===== */
        .home-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: var(--spacing-lg);
            width: 100%;
        }

        .home-card-large {
            grid-column: 1;
            grid-row: 1 / 3;
            background: linear-gradient(135deg, #0066cc 0%, #0099ff 100%);
            border-radius: var(--border-radius);
            padding: var(--spacing-xl);
            color: white;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            cursor: pointer;
            transition: all 0.3s ease;
            min-height: 320px;
        }

        .home-card-large:hover {
            transform: translateY(-4px);
            box-shadow: 0 15px 40px rgba(0, 102, 204, 0.3);
        }

        .home-card-large-title {
            font-size: 24px;
            font-weight: bold;
            line-height: 1.3;
        }

        .home-card-large-subtitle {
            font-size: 13px;
            opacity: 0.95;
        }

        .home-card-small {
            background: linear-gradient(135deg, #0066cc 0%, #0099ff 100%);
            border-radius: var(--border-radius);
            padding: var(--spacing-xl);
            color: white;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
            min-height: 150px;
        }

        .home-card-small:hover {
            transform: translateY(-4px);
            box-shadow: 0 15px 40px rgba(0, 102, 204, 0.3);
        }

        .home-card-small-title {
            font-size: 20px;
            font-weight: bold;
        }

        /* ===== 診断前画面 ===== */
        .before-diagnosis {
            text-align: center;
            padding: var(--spacing-xl) var(--spacing-lg);
        }

        .before-diagnosis-icon {
            font-size: 64px;
            margin-bottom: var(--spacing-lg);
        }

        .before-diagnosis-title {
            font-size: 24px;
            color: var(--primary-blue);
            font-weight: bold;
            margin-bottom: var(--spacing-md);
        }

        .before-diagnosis-text {
            color: var(--text-light);
            line-height: 1.6;
            font-size: 14px;
            margin-bottom: var(--spacing-xl);
        }

        /* ===== 通知画面 ===== */
        .notification-empty {
            text-align: center;
            padding: var(--spacing-xl) var(--spacing-lg);
        }

        .notification-icon {
            font-size: 64px;
            margin-bottom: var(--spacing-lg);
        }

        .notification-title {
            font-size: 18px;
            color: var(--text-dark);
            font-weight: bold;
            margin-bottom: var(--spacing-md);
        }

        .notification-text {
            color: var(--text-light);
            line-height: 1.6;
            font-size: 14px;
            margin-bottom: var(--spacing-xl);
        }

        /* ===== ボタン ===== */
        button {
            font-size: 16px;
            font-weight: bold;
            border: none;
            border-radius: var(--border-radius);
            padding: 14px 24px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-family: inherit;
        }

        .btn-primary {
            background: linear-gradient(135deg, #0066cc 0%, #0099ff 100%);
            color: white;
            width: 100%;
            margin-bottom: var(--spacing-md);
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 30px rgba(0, 102, 204, 0.3);
        }

        .btn-primary:active {
            transform: translateY(0);
        }

        .btn-secondary {
            background: var(--light-blue);
            color: var(--primary-blue);
            width: 100%;
            margin-top: var(--spacing-md);
        }

        .btn-secondary:hover {
            background: #cce5ff;
        }

        /* ===== 質問画面 ===== */
        .progress-bar {
            background: var(--light-blue);
            height: 8px;
            position: relative;
            overflow: hidden;
            margin-bottom: 0;
            width: 100%;
        }

        .progress-fill {
            background: linear-gradient(90deg, #0066cc 0%, #0099ff 100%);
            height: 100%;
            transition: width 0.3s ease;
        }

        .progress-info {
            padding: var(--spacing-md) var(--spacing-xl);
            text-align: center;
            font-size: 13px;
            color: var(--text-light);
            font-weight: 500;
        }

        .question-container {
            padding: 0 var(--spacing-xl) var(--spacing-xl);
            flex: 1;
        }

        .question-title {
            font-size: 18px;
            color: var(--text-dark);
            font-weight: bold;
            margin-bottom: var(--spacing-lg);
            line-height: 1.6;
        }

        .choices {
            display: flex;
            flex-direction: column;
            gap: var(--spacing-md);
        }

        .choice-btn {
            background: white;
            border: 2px solid #e0e0e0;
            color: var(--text-dark);
            text-align: left;
            padding: var(--spacing-md) var(--spacing-lg);
            border-radius: var(--border-radius);
            font-size: 14px;
            line-height: 1.5;
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .choice-btn:hover {
            border-color: var(--primary-blue);
            background: var(--light-blue);
        }

        .choice-btn.selected {
            border-color: var(--primary-blue);
            background: var(--primary-blue);
            color: white;
        }

        .choice-label {
            display: inline-block;
            font-weight: bold;
            margin-right: var(--spacing-sm);
            min-width: 20px;
        }

        .next-button-container {
            margin-top: var(--spacing-xl);
            padding: 0 var(--spacing-xl) var(--spacing-xl);
        }

        /* ===== ���果画面 ===== */
        .result-wrapper {
            width: 100%;
        }

        .result-header {
            text-align: center;
            padding-bottom: var(--spacing-lg);
        }

        .result-type-icon {
            font-size: 48px;
            margin-bottom: var(--spacing-md);
            display: block;
            min-height: 48px;
        }

        .result-type-name {
            font-size: 28px;
            color: var(--primary-blue);
            font-weight: bold;
            margin-bottom: var(--spacing-sm);
            display: block;
            min-height: 36px;
        }

        .result-type-ja {
            font-size: 14px;
            color: var(--text-light);
            font-weight: normal;
            display: block;
            min-height: 18px;
        }

        .result-section {
            margin-bottom: var(--spacing-lg);
        }

        .result-section-title {
            font-size: 12px;
            color: var(--primary-blue);
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: var(--spacing-sm);
        }

        .result-section-content {
            background: var(--light-blue);
            border-left: 4px solid var(--primary-blue);
            padding: var(--spacing-lg);
            border-radius: 8px;
            font-size: 14px;
            color: var(--text-dark);
            line-height: 1.7;
        }

        .action-card {
            background: #fffbf0;
            border: 2px solid #ffc966;
            border-radius: var(--border-radius);
            padding: var(--spacing-lg);
            margin-bottom: var(--spacing-lg);
        }

        .action-card-title {
            font-size: 12px;
            color: #ff9800;
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: var(--spacing-sm);
        }

        .action-card-content {
            font-size: 14px;
            color: var(--text-dark);
            font-weight: 500;
            line-height: 1.7;
        }

        .internship-card {
            background: #f0f8ff;
            border: 2px solid #0099ff;
            border-radius: var(--border-radius);
            padding: var(--spacing-lg);
            margin-bottom: var(--spacing-lg);
        }

        .internship-card-title {
            font-size: 12px;
            color: var(--primary-blue);
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: var(--spacing-md);
        }

        .internship-item {
            margin-bottom: var(--spacing-md);
            padding: var(--spacing-md);
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .internship-item:hover {
            background: #e6f2ff;
        }

        .internship-item:last-child {
            margin-bottom: 0;
        }

        .internship-company {
            font-weight: bold;
            color: var(--primary-blue);
            font-size: 14px;
            margin-bottom: var(--spacing-sm);
        }

        .internship-role {
            color: var(--text-light);
            font-size: 13px;
            line-height: 1.5;
        }

        .result-buttons {
            display: grid;
            gap: var(--spacing-md);
            padding-bottom: var(--spacing-lg);
        }

        /* ===== 申し込み確認画面 ===== */
        .apply-confirmation {
            text-align: center;
        }

        .apply-confirmation-icon {
            font-size: 64px;
            margin-bottom: var(--spacing-lg);
            animation: bounceIn 0.6s ease-out;
        }

        @keyframes bounceIn {
            0% {
                transform: scale(0);
            }
            50% {
                transform: scale(1.1);
            }
            100% {
                transform: scale(1);
            }
        }

        .apply-confirmation-title {
            font-size: 24px;
            color: var(--primary-blue);
            font-weight: bold;
            margin-bottom: var(--spacing-md);
        }

        .apply-confirmation-text {
            color: var(--text-light);
            line-height: 1.8;
            margin-bottom: var(--spacing-xl);
            font-size: 14px;
        }

        .applied-company-info {
            background: var(--light-blue);
            padding: var(--spacing-lg);
            border-radius: var(--border-radius);
            margin-bottom: var(--spacing-xl);
            border-left: 4px solid var(--primary-blue);
            text-align: left;
        }

        .applied-company-name {
            font-size: 18px;
            font-weight: bold;
            color: var(--primary-blue);
            margin-bottom: var(--spacing-sm);
        }

        .applied-company-role {
            color: var(--text-dark);
            font-size: 14px;
            line-height: 1.6;
        }

        /* ===== レスポンシブ ===== */
        @media (max-width: 600px) {
            .container {
                border-radius: 0;
                max-height: 100vh;
            }

            .header {
                padding: var(--spacing-md) var(--spacing-lg);
            }

            body {
                padding: 0;
            }
        }

        .hidden {
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- ===== ヘッダー ===== -->
        <div class="header">
            <div class="header-left">
                <div class="header-tag">「自己ナビ！」</div>
            </div>
            <div class="header-right">
                <div class="header-title">CLARK ambitious テスト</div>
                <div class="header-subtitle">デモ版</div>
            </div>
        </div>

        <!-- ===== コンテンツエリア ===== -->
        <div class="content-wrapper">
            <!-- ===== ホーム画面 ===== -->
            <div class="content active" id="homeScreen">
                <div class="home-grid">
                    <!-- 診断スタートカード -->
                    <div class="home-card-large" onclick="startTest()">
                        <div>
                            <div class="home-card-large-title">診断スタート！</div>
                            <div class="home-card-large-subtitle">CLARK ambitious<br>テスト</div>
                        </div>
                    </div>

                    <!-- 振り返りカード -->
                    <div class="home-card-small" id="reflectionCard" onclick="handleReflectionClick()" style="cursor: pointer;">
                        <div class="home-card-small-title">振り返り</div>
                    </div>

                    <!-- お知らせカード -->
                    <div class="home-card-small" onclick="showNotification()" style="cursor: pointer;">
                        <div class="home-card-small-title">お知らせ</div>
                    </div>
                </div>
            </div>

            <!-- ===== 診断前画面 ===== -->
            <div class="content" id="beforeDiagnosisScreen">
                <div class="before-diagnosis">
                    <div class="before-diagnosis-icon">📋</div>
                    <div class="before-diagnosis-title">診断前です</div>
                    <div class="before-diagnosis-text">
                        まだ診断を実施していません。<br>
                        診断スタートボタンから始めてみましょう！
                    </div>
                    <button class="btn-primary" onclick="backToHome()">ホームに戻る</button>
                </div>
            </div>

            <!-- ===== 質問画面 ===== -->
            <div class="content" id="questionScreen">
                <div class="progress-bar">
                    <div class="progress-fill" id="progressFill" style="width: 20%;"></div>
                </div>
                <div class="progress-info">
                    <span id="progressText">1</span>/5
                </div>

                <div class="question-container">
                    <div class="question-title" id="questionTitle"></div>
                    <div class="choices" id="choicesContainer"></div>
                </div>

                <div class="next-button-container">
                    <button class="btn-primary" id="nextButton" onclick="nextQuestion()" style="display: none;">
                        次へ →
                    </button>
                </div>
            </div>

            <!-- ===== 結果画面 ===== -->
            <div class="content" id="resultScreen">
                <div class="result-wrapper">
                    <div class="result-header">
                        <div class="result-type-icon" id="resultIcon"></div>
                        <div class="result-type-name" id="resultTypeKanji"></div>
                        <div class="result-type-ja" id="resultTypeSubtitle"></div>
                    </div>

                    <div class="result-section">
                        <div class="result-section-title">特徴</div>
                        <div class="result-section-content" id="resultFeature"></div>
                    </div>

                    <div class="result-section">
                        <div class="result-section-title">向いてる職種</div>
                        <div class="result-section-content" id="resultOccupation"></div>
                    </div>

                    <div class="action-card">
                        <div class="action-card-title">📍 次の一歩（Next Action）</div>
                        <div class="action-card-content" id="resultAction"></div>
                    </div>

                    <div class="internship-card">
                        <div class="internship-card-title">💼 おすすめのインターン先</div>
                        <div id="internshipList"></div>
                    </div>

                    <div class="result-buttons">
                        <button class="btn-primary" onclick="backToHome()">ホームに戻る</button>
                    </div>
                </div>
            </div>

            <!-- ===== 前回の結果表示 ===== -->
            <div class="content" id="previousResultScreen">
                <div class="result-wrapper">
                    <div class="result-header">
                        <div class="result-type-icon" id="prevResultIcon"></div>
                        <div class="result-type-name" id="prevResultTypeKanji"></div>
                        <div class="result-type-ja" id="prevResultTypeSubtitle"></div>
                    </div>

                    <div class="result-section">
                        <div class="result-section-title">特徴</div>
                        <div class="result-section-content" id="prevResultFeature"></div>
                    </div>

                    <div class="result-section">
                        <div class="result-section-title">向いてる職種</div>
                        <div class="result-section-content" id="prevResultOccupation"></div>
                    </div>

                    <div class="action-card">
                        <div class="action-card-title">📍 次の一歩（Next Action）</div>
                        <div class="action-card-content" id="prevResultAction"></div>
                    </div>

                    <div class="internship-card">
                        <div class="internship-card-title">💼 おすすめのインターン先</div>
                        <div id="prevInternshipList"></div>
                    </div>

                    <div class="result-buttons">
                        <button class="btn-primary" onclick="backToHome()">ホームに戻る</button>
                    </div>
                </div>
            </div>

            <!-- ===== お知らせ画面 ===== -->
            <div class="content" id="notificationScreen">
                <div class="notification-empty">
                    <div class="notification-icon">📬</div>
                    <div class="notification-title">お知らせはありません</div>
                    <div class="notification-text">
                        現在、新しいお知らせはありません。<br>
                        今後の最新情報をお待ちください。
                    </div>
                    <button class="btn-primary" onclick="backToHome()">ホームに戻る</button>
                </div>
            </div>

            <!-- ===== 申し込み確認画面 ===== -->
            <div class="content" id="applyScreen">
                <div class="apply-confirmation">
                    <div class="apply-confirmation-icon">✅</div>
                    <div class="apply-confirmation-title">申し込みが完了しました！</div>
                    <div class="apply-confirmation-text">
                        選考チームより3営業日以内に<br>メールでご連絡させていただきます
                    </div>
                    <div class="applied-company-info">
                        <div class="applied-company-name" id="appliedCompanyName"></div>
                        <div class="applied-company-role" id="appliedCompanyRole"></div>
                    </div>
                    <p style="color: var(--text-light); font-size: 13px; margin-bottom: var(--spacing-xl);">
                        次のステップ：選考スケジュール確認メールをお待ちください
                    </p>
                    <button class="btn-primary" onclick="backToHome()">ホームに戻る</button>
                </div>
            </div>
        </div>
    </div>

    <script>
        // ===== データ定義 =====
        const questions = [
            {
                id: 1,
                text: "新しいことに挑戦する機会があったら？",
                choices: [
                    { label: "A", text: "まずやってみたい", key: "A" },
                    { label: "B", text: "情報を集めてから判断", key: "B" },
                    { label: "C", text: "誰かと一緒なら挑戦する", key: "C" },
                    { label: "D", text: "自分の役割が明確ならやる", key: "D" },
                    { label: "E", text: "将来につながるなら挑戦する", key: "E" }
                ]
            },
            {
                id: 2,
                text: "グループ活動で自然と取るポジションは？",
                choices: [
                    { label: "A", text: "最初に動き出す人", key: "A" },
                    { label: "B", text: "企画や分析をする人", key: "B" },
                    { label: "C", text: "まとめ役・盛り上げ役", key: "C" },
                    { label: "D", text: "スケジュール管理する人", key: "D" },
                    { label: "E", text: "全体の方向性を考える人", key: "E" }
                ]
            },
            {
                id: 3,
                text: "将来の働き方で一番大事なのは？",
                choices: [
                    { label: "A", text: "ワクワクするか", key: "A" },
                    { label: "B", text: "専門性が高まるか", key: "B" },
                    { label: "C", text: "人とのつながり", key: "C" },
                    { label: "D", text: "安定・信頼", key: "D" },
                    { label: "E", text: "成長できる環境", key: "E" }
                ]
            },
            {
                id: 4,
                text: "問題が起きたときどうする？",
                choices: [
                    { label: "A", text: "すぐ動く", key: "A" },
                    { label: "B", text: "原因を分析する", key: "B" },
                    { label: "C", text: "周りに相談する", key: "C" },
                    { label: "D", text: "役割を整理する", key: "D" },
                    { label: "E", text: "長期的に解決策を考える", key: "E" }
                ]
            },
            {
                id: 5,
                text: "自分が評価されたいポイントは？",
                choices: [
                    { label: "A", text: "行動力", key: "A" },
                    { label: "B", text: "頭の良さ", key: "B" },
                    { label: "C", text: "コミュニケーション力", key: "C" },
                    { label: "D", text: "信頼性", key: "D" },
                    { label: "E", text: "成長力", key: "E" }
                ]
            }
        ];

        const results = {
            A: {
                icon: "🚀",
                typeKanji: "開拓者",
                typeEn: "Frontier",
                subtitle: "挑戦駆動",
                feature: "行動で道を切り開く。未知を怖がらない。好奇心が強く、とにかく試してみることで世界を広げるタイプです。",
                occupation: "新規事業、営業、起業、企画、マーケティング",
                action: "3日以内に「初めての体験」を1つ申し込む。セミナー、ワークショップ、新しいスポーツなど、何でもOK。行動が全てを変えます。",
                internships: [
                    { company: "◆▲株式会社", role: "事業開発インターン - スタートアップの立ち上げからMVP開���までを体験" },
                    { company: "●■株式会社", role: "営業インターン - 新規クライアント開拓と提案営業の実践" },
                    { company: "◇▲株式会社", role: "新規事業企画インターン - 次世代プロダクトの企画・設計に従事" }
                ]
            },
            B: {
                icon: "🧠",
                typeKanji: "分析者",
                typeEn: "Analyst",
                subtitle: "論理駆動",
                feature: "構造化・分析・最適化が得意。複雑な問題を整理し、最良の解を見つけることが得意。論理的思考力が強みです。",
                occupation: "データ分析、IT/開発、研究、経理/財務、経営企画",
                action: "興味分野を1つ決め、情報収集→1枚にまとめる。知識を整理することで専門性が磨かれます。",
                internships: [
                    { company: "▲■株式会社", role: "データ分析インターン - ビッグデータから経営課題の解決策を導き出す" },
                    { company: "●▲株式会社", role: "ソフトウェア開発インターン - Pythonで金融予測モデルの開発に参画" },
                    { company: "◆●株式会社", role: "経営企画インターン - 企業戦略の分析・立案支援に従事" }
                ]
            },
            C: {
                icon: "🎤",
                typeKanji: "繋ぎ手",
                typeEn: "Connector",
                subtitle: "発信/関係駆動",
                feature: "人をつなげ、場を動かす。コミュニケーション力が高く、周囲を巻き込んで事を進めるのが得意。",
                occupation: "広報、企画運営、人事、教育、接客、営業",
                action: "誰か1人に「話を聞く」アポを取り、学びをメモ。関係構築が全ての基盤になります。",
                internships: [
                    { company: "◇■株式会社", role: "採用・人材育成インターン - 企業の人材戦略の企画と実行" },
                    { company: "▲◆株式会社", role: "企画運営インターン - 大規模カンファレンスやイベントの企画・進行管理" },
                    { company: "●◇株式会社", role: "広報・ブランディングインターン - SNS戦略とメディア関係構築" }
                ]
            },
            D: {
                icon: "🛡",
                typeKanji: "支え手",
                typeEn: "Balancer",
                subtitle: "責任/安定駆動",
                feature: "信頼を積み上げ、チームを支える。責任感が強く、ルールを守り、堅実に仕事を進めるタイプ。",
                occupation: "公務員、品質管理、事務、運用管理、総務、コンプライアンス",
                action: "生活/学習のルーティンを1つ固定し、1週間続ける。積み重ねることが圧倒的な力になります。",
                internships: [
                    { company: "◆▲株式会社", role: "品質管理・QA インターン - 製品品質基準の策定と改善施策の実行" },
                    { company: "■●株式会社", role: "経理・財務インターン - 決算業務と内部統制システムの運用" },
                    { company: "▲●株式会社", role: "自治体DX推進インターン - 行政プロセスのデジタル化と効率化" }
                ]
            },
            E: {
                icon: "🌱",
                typeKanji: "成長家",
                typeEn: "Growth",
                subtitle: "成長/拡張駆動",
                feature: "伸びしろ重視。成長環境に強く反応し、自分を高めることに喜びを感じる。拡張志向が強い。",
                occupation: "コンサル、マーケティング、PM、グローバル職、経営企画",
                action: "伸ばしたいスキルを1つ決め、30日プランを作る。成長の道筋を引くことで、人生が変わります。",
                internships: [
                    { company: "●■株式会社", role: "経営コンサルティングインターン - グローバル企業の経営課題解決プロジェクトに参画" },
                    { company: "◇▲株式会社", role: "プロダクトマネージャーインターン - SaaS企業の成長戦略の企画・実行" },
                    { company: "■◆株式会社", role: "国際事業開発インターン - アジア太平洋地域での事業拡大を推進" }
                ]
            }
        };

        // ===== 状態管理 =====
        let currentQuestion = 0;
        let answers = { A: 0, B: 0, C: 0, D: 0, E: 0 };
        let selectedAnswers = {};
        let currentResultKey = null;
        let previousResultKey = localStorage.getItem('previousResultKey');

        // ===== 画面遷移 =====
        function showScreen(screenId) {
            document.querySelectorAll('.content').forEach(el => el.classList.remove('active'));
            document.getElementById(screenId).classList.add('active');
        }

        function initializeHome() {
            const reflectionCard = document.getElementById('reflectionCard');
            
            if (previousResultKey && results[previousResultKey]) {
                reflectionCard.style.opacity = '1';
                reflectionCard.style.pointerEvents = 'auto';
            } else {
                reflectionCard.style.opacity = '0.5';
                reflectionCard.style.pointerEvents = 'none';
            }
        }

        function handleReflectionClick() {
            if (!previousResultKey || !results[previousResultKey]) {
                showScreen('beforeDiagnosisScreen');
            } else {
                showPreviousResult();
            }
        }

        function startTest() {
            currentQuestion = 0;
            answers = { A: 0, B: 0, C: 0, D: 0, E: 0 };
            selectedAnswers = {};
            showScreen('questionScreen');
            loadQuestion();
        }

        function loadQuestion() {
            const question = questions[currentQuestion];
            const progressPercent = ((currentQuestion + 1) / 5) * 100;

            document.getElementById('progressFill').style.width = progressPercent + '%';
            document.getElementById('progressText').textContent = currentQuestion + 1;
            document.getElementById('questionTitle').textContent = question.text;

            const choicesContainer = document.getElementById('choicesContainer');
            choicesContainer.innerHTML = '';

            question.choices.forEach((choice, index) => {
                const btn = document.createElement('button');
                btn.className = 'choice-btn';
                btn.innerHTML = `<span class="choice-label">${choice.label}</span>${choice.text}`;
                btn.onclick = () => selectChoice(choice.key, btn);

                if (selectedAnswers[currentQuestion] === choice.key) {
                    btn.classList.add('selected');
                }

                choicesContainer.appendChild(btn);
            });

            updateNextButton();
        }

        function selectChoice(key, btn) {
            document.querySelectorAll('.choice-btn').forEach(el => el.classList.remove('selected'));
            btn.classList.add('selected');
            selectedAnswers[currentQuestion] = key;
            updateNextButton();
        }

        function updateNextButton() {
            const nextButton = document.getElementById('nextButton');
            if (selectedAnswers[currentQuestion]) {
                nextButton.style.display = 'block';
            } else {
                nextButton.style.display = 'none';
            }
        }

        function nextQuestion() {
            const selectedKey = selectedAnswers[currentQuestion];
            answers[selectedKey]++;
            currentQuestion++;

            if (currentQuestion < 5) {
                loadQuestion();
            } else {
                showResult();
            }
        }

        // ===== 診断ロジック =====
        function showResult() {
            const maxCount = Math.max(...Object.values(answers));
            let resultKey = null;
            const maxKeys = Object.keys(answers).filter(key => answers[key] === maxCount);

            if (maxKeys.length === 1) {
                resultKey = maxKeys[0];
            } else {
                resultKey = selectedAnswers[2];
            }

            currentResultKey = resultKey;
            localStorage.setItem('previousResultKey', resultKey);
            previousResultKey = resultKey;
            displayResult(resultKey);
        }

        function displayResult(typeKey) {
            const result = results[typeKey];

            document.getElementById('resultIcon').textContent = result.icon;
            document.getElementById('resultTypeKanji').textContent = result.typeKanji;
            document.getElementById('resultTypeSubtitle').textContent = result.subtitle;
            document.getElementById('resultFeature').innerHTML = result.feature;
            document.getElementById('resultOccupation').innerHTML = result.occupation;
            document.getElementById('resultAction').innerHTML = result.action;

            const internshipList = document.getElementById('internshipList');
            internshipList.innerHTML = '';
            result.internships.forEach(internship => {
                const div = document.createElement('div');
                div.className = 'internship-item';
                div.onclick = () => applyInternship(internship.company, internship.role);
                div.innerHTML = `
                    <div class="internship-company">${internship.company}</div>
                    <div class="internship-role">${internship.role}</div>
                `;
                internshipList.appendChild(div);
            });

            showScreen('resultScreen');
        }

        function showPreviousResult() {
            if (!previousResultKey || !results[previousResultKey]) {
                return;
            }

            const result = results[previousResultKey];

            document.getElementById('prevResultIcon').textContent = result.icon;
            document.getElementById('prevResultTypeKanji').textContent = result.typeKanji;
            document.getElementById('prevResultTypeSubtitle').textContent = result.subtitle;
            document.getElementById('prevResultFeature').innerHTML = result.feature;
            document.getElementById('prevResultOccupation').innerHTML = result.occupation;
            document.getElementById('prevResultAction').innerHTML = result.action;

            const prevInternshipList = document.getElementById('prevInternshipList');
            prevInternshipList.innerHTML = '';
            result.internships.forEach(internship => {
                const div = document.createElement('div');
                div.className = 'internship-item';
                div.onclick = () => applyInternship(internship.company, internship.role);
                div.innerHTML = `
                    <div class="internship-company">${internship.company}</div>
                    <div class="internship-role">${internship.role}</div>
                `;
                prevInternshipList.appendChild(div);
            });

            showScreen('previousResultScreen');
        }

        function showNotification() {
            showScreen('notificationScreen');
        }

        function applyInternship(company, role) {
            document.getElementById('appliedCompanyName').textContent = company;
            document.getElementById('appliedCompanyRole').textContent = role;
            showScreen('applyScreen');
        }

        function backToHome() {
            showScreen('homeScreen');
            initializeHome();
        }

        // ===== 初期化 =====
        window.addEventListener('load', () => {
            initializeHome();
        });

        initializeHome();
    </script>
</body>
</html>
