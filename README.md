index.html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>郷土料理科学研究プラットフォーム - 科学的根拠に基づく日本の食文化</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Helvetica Neue', Arial, 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', Meiryo, sans-serif;
            line-height: 1.6;
            color: #333;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        header {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            box-shadow: 0 2px 20px rgba(0, 0, 0, 0.1);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            transition: all 0.3s ease;
        }
        
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 0;
        }
        
        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            color: #4a5568;
            text-decoration: none;
        }
        
        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
            align-items: center;
        }
        
        .nav-links a {
            text-decoration: none;
            color: #4a5568;
            font-weight: 500;
            transition: color 0.3s ease;
        }
        
        .nav-links a:hover {
            color: #667eea;
        }
        
        .post-btn {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            padding: 10px 20px;
            border-radius: 25px;
            text-decoration: none;
            font-weight: bold;
            transition: all 0.3s ease;
        }
        
        .post-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        
        main {
            margin-top: 80px;
            padding: 2rem 0;
        }
        
        .hero {
            text-align: center;
            padding: 4rem 0;
            color: white;
            margin-bottom: 3rem;
        }
        
        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 1rem;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }
        
        .hero p {
            font-size: 1.3rem;
            margin-bottom: 2rem;
            opacity: 0.9;
        }
        
        .hero-stats {
            display: flex;
            justify-content: center;
            gap: 3rem;
            margin-top: 2rem;
        }
        
        .hero-stat {
            text-align: center;
        }
        
        .hero-stat-number {
            font-size: 2.5rem;
            font-weight: bold;
            display: block;
        }
        
        .hero-stat-label {
            font-size: 1rem;
            opacity: 0.8;
        }
        
        /* 投稿フォームセクション */
        .post-section {
            background: white;
            border-radius: 20px;
            padding: 2rem;
            margin: 2rem 0;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.1);
            display: none;
        }
        
        .post-section.active {
            display: block;
        }
        
        .form-group {
            margin-bottom: 1.5rem;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: bold;
            color: #4a5568;
        }
        
        .form-group input,
        .form-group textarea,
        .form-group select {
            width: 100%;
            padding: 12px;
            border: 2px solid #e2e8f0;
            border-radius: 8px;
            font-size: 1rem;
            transition: border-color 0.3s ease;
        }
        
        .form-group input:focus,
        .form-group textarea:focus,
        .form-group select:focus {
            outline: none;
            border-color: #667eea;
        }
        
        .form-group textarea {
            min-height: 120px;
            resize: vertical;
        }
        
        .form-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1rem;
        }
        
        .btn {
            padding: 12px 24px;
            border: none;
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            margin-right: 1rem;
        }
        
        .btn-primary {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
        }
        
        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        
        .btn-secondary {
            background: #e2e8f0;
            color: #4a5568;
        }
        
        /* 検索・フィルターセクション */
        .search-section {
            background: white;
            border-radius: 20px;
            padding: 2rem;
            margin: 2rem 0;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.1);
        }
        
        .search-box-container {
            position: relative;
            max-width: 600px;
            margin: 0 auto 2rem;
        }
        
        .search-box {
            width: 100%;
            padding: 15px 20px 15px 50px;
            border: 2px solid #e2e8f0;
            border-radius: 50px;
            font-size: 1rem;
            outline: none;
            transition: all 0.3s ease;
        }
        
        .search-box:focus {
            border-color: #667eea;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
        }
        
        .search-icon {
            position: absolute;
            left: 15px;
            top: 50%;
            transform: translateY(-50%);
            color: #666;
            font-size: 1.2rem;
        }
        
        .filter-section {
            margin-bottom: 2rem;
        }
        
        .filter-title {
            font-weight: bold;
            margin-bottom: 1rem;
            color: #4a5568;
        }
        
        .filter-buttons {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            justify-content: center;
        }
        
        .filter-btn {
            padding: 8px 16px;
            border: 2px solid #667eea;
            background: transparent;
            color: #667eea;
            border-radius: 25px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 0.9rem;
        }
        
        .filter-btn:hover,
        .filter-btn.active {
            background: #667eea;
            color: white;
        }
        
        /* 記事表示 */
        .articles-section {
            background: white;
            border-radius: 20px;
            padding: 3rem;
            margin: 2rem 0;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.1);
        }
        
        .section-header {
            text-align: center;
            margin-bottom: 3rem;
        }
        
        .section-title {
            font-size: 2.5rem;
            color: #4a5568;
            margin-bottom: 1rem;
        }
        
        .section-subtitle {
            font-size: 1.1rem;
            color: #666;
        }
        
        .articles-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(380px, 1fr));
            gap: 2rem;
        }
        
        .article-card {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
            cursor: pointer;
            position: relative;
        }
        
        .article-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15);
        }
        
        .article-image {
            height: 200px;
            background: linear-gradient(45deg, #ffeaa7, #fab1a0);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            color: white;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
            position: relative;
        }
        
        .article-stats {
            position: absolute;
            top: 10px;
            right: 10px;
            background: rgba(255, 255, 255, 0.9);
            padding: 5px 10px;
            border-radius: 15px;
            font-size: 0.8rem;
            color: #666;
        }
        
        .article-badges {
            position: absolute;
            top: 10px;
            left: 10px;
            display: flex;
            gap: 5px;
            flex-wrap: wrap;
        }
        
        .badge {
            background: rgba(102, 126, 234, 0.9);
            color: white;
            padding: 3px 8px;
            border-radius: 12px;
            font-size: 0.7rem;
            font-weight: bold;
        }
        
        .badge-prefecture {
            background: rgba(255, 107, 107, 0.9);
        }
        
        .badge-cuisine {
            background: rgba(16, 185, 129, 0.9);
        }
        
        .badge-ingredient {
            background: rgba(245, 158, 11, 0.9);
        }
        
        .article-content {
            padding: 1.5rem;
        }
        
        .article-meta {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1rem;
            font-size: 0.9rem;
            color: #666;
        }
        
        .article-title {
            font-size: 1.3rem;
            font-weight: bold;
            color: #4a5568;
            margin-bottom: 0.8rem;
        }
        
        .article-description {
            color: #666;
            margin-bottom: 1rem;
            line-height: 1.5;
        }
        
        .article-research {
            background: #f8f9ff;
            padding: 1rem;
            border-radius: 10px;
            border-left: 4px solid #667eea;
            margin: 1rem 0;
        }
        
        .research-title {
            font-weight: bold;
            font-size: 0.9rem;
            color: #4a5568;
            margin-bottom: 0.5rem;
        }
        
        .article-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: 1rem;
            padding-top: 1rem;
            border-top: 1px solid #e2e8f0;
        }
        
        .article-actions {
            display: flex;
            gap: 0.5rem;
        }
        
        .action-btn {
            padding: 5px 12px;
            border: 1px solid #e2e8f0;
            background: white;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 0.8rem;
        }
        
        .action-btn:hover {
            background: #f8f9ff;
            border-color: #667eea;
        }
        
        .comments-count {
            color: #667eea;
            font-size: 0.9rem;
            font-weight: bold;
            cursor: pointer;
        }
        
        /* モーダル */
        .modal {
            display: none;
            position: fixed;
            z-index: 2000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            backdrop-filter: blur(5px);
        }
        
        .modal-content {
            background-color: white;
            margin: 2% auto;
            padding: 0;
            border-radius: 20px;
            width: 90%;
            max-width: 800px;
            max-height: 90vh;
            overflow-y: auto;
            position: relative;
        }
        
        .modal-header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 2rem;
            border-radius: 20px 20px 0 0;
            position: relative;
        }
        
        .modal-body {
            padding: 2rem;
        }
        
        .close {
            position: absolute;
            right: 1rem;
            top: 1rem;
            font-size: 2rem;
            cursor: pointer;
            color: white;
            transition: color 0.3s ease;
        }
        
        .close:hover {
            color: #ddd;
        }
        
        /* 分析セクション */
        .analytics-section {
            background: white;
            border-radius: 20px;
            padding: 2rem;
            margin: 2rem 0;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.1);
        }
        
        .popular-articles {
            margin-top: 2rem;
        }
        
        .popular-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem;
            border-bottom: 1px solid #e2e8f0;
        }
        
        .popular-item:last-child {
            border-bottom: none;
        }
        
        .popular-rank {
            font-size: 1.2rem;
            font-weight: bold;
            color: #667eea;
            margin-right: 1rem;
        }
        
        .popular-title {
            flex: 1;
            font-weight: 500;
        }
        
        .popular-views {
            color: #666;
            font-size: 0.9rem;
        }
        
        /* レスポンシブ */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 2.5rem;
            }
            
            .hero-stats {
                flex-direction: column;
                gap: 1rem;
            }
            
            .nav-links {
                display: none;
            }
            
            .articles-grid {
                grid-template-columns: 1fr;
            }
            
            .form-row {
                grid-template-columns: 1fr;
            }
            
            .filter-buttons {
                justify-content: flex-start;
            }
            
            .modal-content {
                width: 95%;
                margin: 5% auto;
            }
        }
        
        /* アニメーション */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        .fade-in {
            animation: fadeInUp 0.6s ease;
        }
        
        /* 成功メッセージ */
        .success-message {
            background: #10b981;
            color: white;
            padding: 1rem;
            border-radius: 8px;
            margin: 1rem 0;
            text-align: center;
            display: none;
        }
    </style>
</head>
<body>
    <header>
        <nav class="container">
            <a href="#" class="logo">🍱 郷土料理科学研究プラットフォーム</a>
            <ul class="nav-links">
                <li><a href="#home" onclick="showSection('home')">ホーム</a></li>
                <li><a href="#articles" onclick="showSection('articles')">記事一覧</a></li>
                <li><a href="#analytics" onclick="showSection('analytics')">人気記事</a></li>
                <li><a href="#post" class="post-btn" onclick="showSection('post')">記事を投稿</a></li>
            </ul>
        </nav>
    </header>

    <main class="container">
        <!-- ホームセクション -->
        <section id="home" class="hero">
            <h1>🔬 郷土料理科学研究プラットフォーム</h1>
            <p>科学的根拠に基づく日本の食文化研究・情報共有サイト</p>
            <div class="hero-stats">
                <div class="hero-stat">
                    <span class="hero-stat-number" id="totalArticles">0</span>
                    <span class="hero-stat-label">研究記事数</span>
                </div>
                <div class="hero-stat">
                    <span class="hero-stat-number" id="totalViews">0</span>
                    <span class="hero-stat-label">総閲覧数</span>
                </div>
                <div class="hero-stat">
                    <span class="hero-stat-number" id="totalComments">0</span>
                    <span class="hero-stat-label">コメント数</span>
                </div>
            </div>
        </section>

        <!-- 記事投稿セクション -->
        <section id="post-section" class="post-section">
            <h2>📝 新しい研究記事を投稿</h2>
            <p style="color: #666; margin-bottom: 2rem;">科学的根拠に基づいた郷土料理の研究記事を投稿してください。投稿された記事は全ての読者が閲覧できます。</p>
            
            <div class="success-message" id="successMessage">
                記事が正常に投稿されました！全ての読者が閲覧できます。
            </div>
            
            <form id="articleForm">
                <div class="form-group">
                    <label for="title">記事タイトル *</label>
                    <input type="text" id="title" name="title" placeholder="例：青森県の津軽味噌における乳酸菌の機能性研究" required>
                </div>
                
                <div class="form-row">
                    <div class="form-group">
                        <label for="prefecture">都道府県 *</label>
                        <select id="prefecture" name="prefecture" required>
                            <option value="">選択してください</option>
                            <option value="北海道">北海道</option>
                            <option value="青森県">青森県</option>
                            <option value="岩手県">岩手県</option>
                            <option value="宮城県">宮城県</option>
                            <option value="秋田県">秋田県</option>
                            <option value="山形県">山形県</option>
                            <option value="福島県">福島県</option>
                            <option value="茨城県">茨城県</option>
                            <option value="栃木県">栃木県</option>
                            <option value="群馬県">群馬県</option>
                            <option value="埼玉県">埼玉県</option>
                            <option value="千葉県">千葉県</option>
                            <option value="東京都">東京都</option>
                            <option value="神奈川県">神奈川県</option>
                            <option value="新潟県">新潟県</option>
                            <option value="富山県">富山県</option>
                            <option value="石川県">石川県</option>
                            <option value="福井県">福井県</option>
                            <option value="山梨県">山梨県</option>
                            <option value="長野県">長野県</option>
                            <option value="岐阜県">岐阜県</option>
                            <option value="静岡県">静岡県</option>
                            <option value="愛知県">愛知県</option>
                            <option value="三重県">三重県</option>
                            <option value="滋賀県">滋賀県</option>
                            <option value="京都府">京都府</option>
                            <option value="大阪府">大阪府</option>
                            <option value="兵庫県">兵庫県</option>
                            <option value="奈良県">奈良県</option>
                            <option value="和歌山県">和歌山県</option>
                            <option value="鳥取県">鳥取県</option>
                            <option value="島根県">島根県</option>
                            <option value="岡山県">岡山県</option>
                            <option value="広島県">広島県</option>
                            <option value="山口県">山口県</option>
                            <option value="徳島県">徳島県</option>
                            <option value="香川県">香川県</option>
                            <option value="愛媛県">愛媛県</option>
                            <option value="高知県">高知県</option>
                            <option value="福岡県">福岡県</option>
                            <option value="佐賀県">佐賀県</option>
                            <option value="長崎県">長崎県</option>
                            <option value="熊本県">熊本県</option>
                            <option value="大分県">大分県</option>
                            <option value="宮崎県">宮崎県</option>
                            <option value="鹿児島県">鹿児島県</option>
                            <option value="沖縄県">沖縄県</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="cuisine">郷土料理名 *</label>
                        <input type="text" id="cuisine" name="cuisine" placeholder="例：津軽味噌、博多ラーメン、沖縄そば" required>
                    </div>
                </div>
                
                <div class="form-group">
                    <label for="ingredient">主要食材カテゴリ *</label>
                    <select id="ingredient" name="ingredient" required>
                        <option value="">選択してください</option>
                        <option value="調味料">調味料</option>
                        <option value="野菜">野菜</option>
                        <option value="魚介類">魚介類</option>
                        <option value="肉類">肉類</option>
                        <option value="米・穀物">米・穀物</option>
                        <option value="豆類">豆類</option>
                        <option value="発酵食品">発酵食品</option>
                        <option value="その他">その他</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label for="description">研究概要・記事内容 *</label>
                    <textarea id="description" name="description" placeholder="この郷土料理について、科学的観点から分析した研究内容や栄養学的知見、調理科学的な特徴などを詳しく説明してください..." required></textarea>
                </div>
                
                <div class="form-group">
                    <label for="findings">主要な科学的知見 *</label>
                    <textarea id="findings" name="findings" placeholder="研究で明らかになった科学的事実、栄養成分データ、機能性成分の分析結果などを記載してください..." required></textarea>
                </div>
                
                <div class="form-group">
                    <label for="nutrition">栄養・成分データ</label>
                    <textarea id="nutrition" name="nutrition" placeholder="例：タンパク質 18.5g/100g、ビタミンB1 0.8mg/100g、食物繊維 3.2g/100g、抗酸化活性（DPPH法）IC50=45.2μg/ml"></textarea>
                </div>
                
                <button type="submit" class="btn btn-primary">📤 記事を投稿する</button>
                <button type="button" class="btn btn-secondary" onclick="clearForm()">🗑 クリア</button>
            </form>
        </section>

        <!-- 検索・フィルターセクション -->
        <section class="search-section">
            <h2 style="text-align: center; margin-bottom: 2rem;">🔍 記事検索・フィルター</h2>
            
            <div class="search-box-container">
                <div class="search-icon">🔍</div>
                <input type="text" class="search-box" placeholder="記事タイトル、郷土料理名、食材、研究内容で検索..." id="searchInput">
            </div>
            
            <div class="filter-section">
                <div class="filter-title">📍 都道府県で絞り込み</div>
                <div class="filter-buttons" id="prefectureFilters">
                    <button class="filter-btn active" data-type="prefecture" data-value="all">全て</button>
                </div>
            </div>
            
            <div class="filter-section">
                <div class="filter-title">🍽 食材カテゴリで絞り込み</div>
                <div class="filter-buttons" id="ingredientFilters">
                    <button class="filter-btn active" data-type="ingredient" data-value="all">全て</button>
                    <button class="filter-btn" data-type="ingredient" data-value="調味料">調味料</button>
                    <button class="filter-btn" data-type="ingredient" data-value="野菜">野菜</button>
                    <button class="filter-btn" data-type="ingredient" data-value="魚介類">魚介類</button>
                    <button class="filter-btn" data-type="ingredient" data-value="肉類">肉類</button>
                    <button class="filter-btn" data-type="ingredient" data-value="米・穀物">米・穀物</button>
                    <button class="filter-btn" data-type="ingredient" data-value="発酵食品">発酵食品</button>
                </div>
            </div>
        </section>

        <!-- 記事一覧セクション -->
        <section id="articles-section" class="articles-section">
            <div class="section-header">
                <h2 class="section-title">📚 研究記事一覧</h2>
                <p class="section-subtitle">科学的根拠に基づく郷土料理研究 - 誰でも閲覧・コメント可能</p>
            </div>
            
            <div class="articles-grid" id="articlesGrid">
                <!-- 記事がここに動的に表示されます -->
            </div>
        </section>

        <!-- 人気記事分析セクション -->
        <section id="analytics-section" class="analytics-section" style="display: none;">
            <h2 style="text-align: center; margin-bottom: 2rem;">📊 人気記事分析</h2>
            <div class="popular-articles">
                <h3>👁 閲覧数ランキング</h3>
                <div id="popularArticlesList">
                    <!-- 人気記事がここに表示されます -->
                </div>
            </div>
        </section>
    </main>

    <!-- 記事詳細モーダル -->
    <div id="articleModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <span class="close">&times;</span>
                <div id="modalTitle"></div>
            </div>
            <div class="modal-body">
                <div id="modalContent"></div>
                <!-- Giscusコメントシステム -->
                <div id="giscus-container">
                    <script src="https://giscus.app/client.js"
                            data-repo="a2shinn/scientific-local-cuisine"
                            data-repo-id="R_kgDOPhfkSQ"
                            data-category="General"
                            data-category-id="DIC_kwDOPhfkSc4Cuekx"
                            data-mapping="pathname"
                            data-strict="0"
                            data-reactions-enabled="1"
                            data-emit-metadata="1"
                            data-input-position="top"
                            data-theme="preferred_color_scheme"
                            data-lang="ja"
                            data-loading="lazy"
                            crossorigin="anonymous"
                            async>
                    </script>
                </div>
            </div>
        </div>
    </div>

    <footer style="background: rgba(0, 0, 0, 0.8); color: white; text-align: center; padding: 2rem 0; margin-top: 3rem;">
        <div class="container">
            <p>&copy; 2025 郷土料理科学研究プラットフォーム</p>
            <p>🔬 科学的根拠に基づく食文化研究・情報共有サイト</p>
        </div>
    </footer>

    <script>
        // Airtable設定（実際の値に置き換えてください）
        const AIRTABLE_API_TOKEN = 'patyv6TUbEZKB04Vj.58dc9f613796ad95ca20b1a869321630fef6be0b2cc4ba9359c509a54cb031dd';
        const AIRTABLE_BASE_ID = 'appvr7QVuqnAHHc41';
        const AIRTABLE_TABLE_NAME = 'Articles';

        // グローバル変数
        let articles = [];
        let currentFilters = {
            prefecture: 'all',
            ingredient: 'all',
            search: ''
        };

        // 初期化
        document.addEventListener('DOMContentLoaded', function() {
            setupEventListeners();
            loadArticlesFromAirtable();
            showSection('home');
        });

        // イベントリスナー設定
        function setupEventListeners() {
            // フォーム送信
            document.getElementById('articleForm').addEventListener('submit', handleArticleSubmission);

            // 検索
            document.getElementById('searchInput').addEventListener('input', function() {
                currentFilters.search = this.value.toLowerCase();
                filterArticles();
            });

            // フィルターボタン
            document.querySelectorAll('.filter-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const type = this.getAttribute('data-type');
                    const value = this.getAttribute('data-value');
                    
                    // 同じタイプの他のボタンを非アクティブに
                    document.querySelectorAll(`.filter-btn[data-type="${type}"]`).forEach(b => b.classList.remove('active'));
                    this.classList.add('active');
                    
                    currentFilters[type] = value;
                    filterArticles();
                });
            });

            // モーダル
            document.querySelector('.close').addEventListener('click', closeModal);
            window.addEventListener('click', function(event) {
                const modal = document.getElementById('articleModal');
                if (event.target === modal) {
                    closeModal();
                }
            });
        }

        // セクション表示切り替え
        function showSection(sectionName) {
            // 全セクションを非表示
            document.getElementById('post-section').classList.remove('active');
            document.getElementById('analytics-section').style.display = 'none';
            
            switch(sectionName) {
                case 'post':
                    document.getElementById('post-section').classList.add('active');
                    break;
                case 'analytics':
                    document.getElementById('analytics-section').style.display = 'block';
                    updatePopularArticles();
                    break;
                case 'articles':
                    document.querySelector('#articles-section').scrollIntoView({ behavior: 'smooth' });
                    break;
                case 'home':
                default:
                    document.querySelector('#home').scrollIntoView({ behavior: 'smooth' });
                    break;
            }
        }

        // Airtableから記事を読み込み
        async function loadArticlesFromAirtable() {
            try {
                const response = await fetch(`https://api.airtable.com/v0/${AIRTABLE_BASE_ID}/${AIRTABLE_TABLE_NAME}?sort[0][field]=DateCreated&sort[0][direction]=desc`, {
                    headers: {
                        'Authorization': `Bearer ${AIRTABLE_API_TOKEN}`
                    }
                });
                
                if (response.ok) {
                    const data = await response.json();
                    articles = data.records.map(record => ({
                        id: record.id,
                        ...record.fields,
                        views: record.fields.views || 1
                    }));
                    
                    displayArticles();
                    updateStatistics();
                    updatePrefectureFilters();
                } else {
                    console.error('記事の読み込みに失敗しました');
                    displayEmptyState();
                }
            } catch (error) {
                console.error('エラー:', error);
                displayEmptyState();
            }
        }

        // 記事投稿処理
        async function handleArticleSubmission(e) {
            e.preventDefault();
            
            const formData = new FormData(document.getElementById('articleForm'));
            
            const airtableData = {
                records: [{
                    fields: {
                        Title: formData.get('title'),
                        Prefecture: formData.get('prefecture'),
                        Cuisine: formData.get('cuisine'),
                        Ingredient: formData.get('ingredient'),
                        Description: formData.get('description'),
                        Findings: formData.get('findings'),
                        Nutrition: formData.get('nutrition') || '',
                        DateCreated: new Date().toISOString().split('T')[0],
                        Views: 1
                    }
                }]
            };

            try {
                const response = await fetch(`https://api.airtable.com/v0/${AIRTABLE_BASE_ID}/${AIRTABLE_TABLE_NAME}`, {
                    method: 'POST',
                    headers: {
                        'Authorization': `Bearer ${AIRTABLE_API_TOKEN}`,
                        'Content-Type': 'application/json'
                    },
                    body: JSON.stringify(airtableData)
                });

                if (response.ok) {
                    showSuccessMessage();
                    clearForm();
                    loadArticlesFromAirtable(); // 記事一覧を更新
                    showSection('articles'); // 記事一覧に移動
                } else {
                    throw new Error('投稿に失敗しました');
                }
            } catch (error) {
                alert('投稿中にエラーが発生しました。もう一度お試しください。');
                console.error('Error:', error);
            }
        }

        // 記事表示
        function displayArticles() {
            const articlesGrid = document.getElementById('articlesGrid');
            
            const filteredArticles = articles.filter(article => {
                const matchesSearch = currentFilters.search === '' || 
                    (article.Title && article.Title.toLowerCase().includes(currentFilters.search)) ||
                    (article.Cuisine && article.Cuisine.toLowerCase().includes(currentFilters.search)) ||
                    (article.Description && article.Description.toLowerCase().includes(currentFilters.search));
                
                const matchesPrefecture = currentFilters.prefecture === 'all' || 
                    article.Prefecture === currentFilters.prefecture;
                
                const matchesIngredient = currentFilters.ingredient === 'all' || 
                    article.Ingredient === currentFilters.ingredient;
                
                return matchesSearch && matchesPrefecture && matchesIngredient;
            });
            
            if (filteredArticles.length === 0) {
                displayEmptyState();
                return;
            }
            
            articlesGrid.innerHTML = filteredArticles.map(article => `
                <div class="article-card fade-in" onclick="showArticleModal('${article.id}')">
                    <div class="article-image">🍽
                        <div class="article-badges">
                            <span class="badge badge-prefecture">${article.Prefecture || '未設定'}</span>
                            <span class="badge badge-cuisine">${article.Cuisine || '未設定'}</span>
                            <span class="badge badge-ingredient">${article.Ingredient || '未設定'}</span>
                        </div>
                        <div class="article-stats">👁 ${article.Views || 1}</div>
                    </div>
                    <div class="article-content">
                        <div class="article-meta">
                            <span>${formatDate(article.DateCreated)}</span>
                        </div>
                        <h3 class="article-title">${article.Title || '無題'}</h3>
                        <p class="article-description">${truncateText(article.Description || '', 100)}</p>
                        <div class="article-research">
                            <div class="research-title">🔬 科学的知見</div>
                            <p>${truncateText(article.Findings || '', 80)}</p>
                        </div>
                        <div class="article-footer">
                            <div class="article-actions">
                                <button class="action-btn">📖 詳細を見る</button>
                            </div>
                            <div class="comments-count">💬 コメント</div>
                        </div>
                    </div>
                </div>
            `).join('');
        }

        // 空の状態表示
        function displayEmptyState() {
            const articlesGrid = document.getElementById('articlesGrid');
            articlesGrid.innerHTML = `
                <div style="grid-column: 1/-1; text-align: center; padding: 3rem; color: #666;">
                    <h3>📝 記事が見つかりません</h3>
                    <p style="margin: 1rem 0;">検索条件を変更するか、新しい記事を投稿してみてください。</p>
                    <button class="btn btn-primary" onclick="showSection('post')">記事を投稿する</button>
                </div>
            `;
        }

        // 記事詳細モーダル表示
        async function showArticleModal(articleId) {
            const article = articles.find(a => a.id === articleId);
            if (!article) return;
            
            const modal = document.getElementById('articleModal');
            const modalTitle = document.getElementById('modalTitle');
            const modalContent = document.getElementById('modalContent');
            
            modalTitle.innerHTML = `<h2>${article.Title}</h2>`;
            
            modalContent.innerHTML = `
                <div style="margin-bottom: 2rem;">
                    <div style="display: flex; gap: 0.5rem; margin-bottom: 1rem; flex-wrap: wrap;">
                        <span class="badge badge-prefecture">${article.Prefecture}</span>
                        <span class="badge badge-cuisine">${article.Cuisine}</span>
                        <span class="badge badge-ingredient">${article.Ingredient}</span>
                        <span class="badge">👁 ${article.Views}回閲覧</span>
                        <span class="badge">📅 ${formatDate(article.DateCreated)}</span>
                    </div>
                </div>
                <div style="margin-bottom: 2rem;">
                    <h3>📋 研究概要</h3>
                    <p style="line-height: 1.6;">${article.Description}</p>
                </div>
                <div style="margin-bottom: 2rem;">
                    <h3>🔬 主要な科学的知見</h3>
                    <p style="line-height: 1.6;">${article.Findings}</p>
                </div>
                ${article.Nutrition ? `
                <div style="margin-bottom: 2rem;">
                    <h3>📊 栄養・成分データ</h3>
                    <div style="background: #f0f9ff; padding: 1rem; border-radius: 8px;">
                        <pre style="white-space: pre-wrap; font-family: inherit;">${article.Nutrition}</pre>
                    </div>
                </div>
                ` : ''}
            `;
            
            modal.style.display = 'block';
            document.body.style.overflow = 'hidden';
            
            // 閲覧数更新
            await updateViewCount(articleId);
        }

        // 閲覧数更新
        async function updateViewCount(articleId) {
            const article = articles.find(a => a.id === articleId);
            if (!article) return;
            
            const newViews = (article.Views || 1) + 1;
            
            try {
                await fetch(`https://api.airtable.com/v0/${AIRTABLE_BASE_ID}/${AIRTABLE_TABLE_NAME}/${articleId}`, {
                    method: 'PATCH',
                    headers: {
                        'Authorization': `Bearer ${AIRTABLE_API_TOKEN}`,
                        'Content-Type': 'application/json'
                    },
                    body: JSON.stringify({
                        fields: {
                            Views: newViews
                        }
                    })
                });
                
                // ローカルデータも更新
                article.Views = newViews;
                updateStatistics();
                
            } catch (error) {
                console.error('閲覧数更新エラー:', error);
            }
        }

        // 統計更新
        function updateStatistics() {
            const totalViews = articles.reduce((sum, article) => sum + (article.Views || 1), 0);
            
            document.getElementById('totalArticles').textContent = articles.length;
            document.getElementById('totalViews').textContent = totalViews;
            // コメント数は実装に応じて更新
        }

        // 都道府県フィルター更新
        function updatePrefectureFilters() {
            const prefectures = [...new Set(articles.map(article => article.Prefecture).filter(Boolean))].sort();
            const filtersContainer = document.getElementById('prefectureFilters');
            
            // 既存の全てボタンは残す
            const allButton = filtersContainer.querySelector('[data-value="all"]');
            filtersContainer.innerHTML = '';
            filtersContainer.appendChild(allButton);
            
            // 使用されている都道府県のボタンを追加
            prefectures.forEach(prefecture => {
                const button = document.createElement('button');
                button.className = 'filter-btn';
                button.setAttribute('data-type', 'prefecture');
                button.setAttribute('data-value', prefecture);
                button.textContent = prefecture;
                button.addEventListener('click', function() {
                    document.querySelectorAll('.filter-btn[data-type="prefecture"]').forEach(b => b.classList.remove('active'));
                    this.classList.add('active');
                    currentFilters.prefecture = prefecture;
                    filterArticles();
                });
                filtersContainer.appendChild(button);
            });
        }

        // 人気記事更新
        function updatePopularArticles() {
            const sortedArticles = [...articles].sort((a, b) => (b.Views || 1) - (a.Views || 1)).slice(0, 10);
            const listContainer = document.getElementById('popularArticlesList');
            
            if (sortedArticles.length === 0) {
                listContainer.innerHTML = '<p style="text-align: center; color: #666;">まだ記事がありません</p>';
                return;
            }
            
            listContainer.innerHTML = sortedArticles.map((article, index) => `
                <div class="popular-item" onclick="showArticleModal('${article.id}')">
                    <div class="popular-rank">${index + 1}</div>
                    <div class="popular-title">${article.Title} <span style="color: #667eea;">(${article.Prefecture} - ${article.Cuisine})</span></div>
                    <div class="popular-views">${article.Views || 1}回閲覧</div>
                </div>
            `).join('');
        }

        // フィルタリング
        function filterArticles() {
            displayArticles();
        }

        // モーダル閉じる
        function closeModal() {
            const modal = document.getElementById('articleModal');
            modal.style.display = 'none';
            document.body.style.overflow = 'auto';
        }

        // ユーティリティ関数
        function formatDate(dateString) {
            if (!dateString) return '不明';
            return new Date(dateString).toLocaleDateString('ja-JP');
        }

        function truncateText(text, maxLength) {
            if (!text) return '';
            return text.length > maxLength ? text.substring(0, maxLength) + '...' : text;
        }

        function showSuccessMessage() {
            const message = document.getElementById('successMessage');
            message.style.display = 'block';
            setTimeout(() => {
                message.style.display = 'none';
            }, 5000);
        }

        function clearForm() {
            document.getElementById('articleForm').reset();
        }
    </script>
</body>
</html>
