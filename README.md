shopify-ai-analytics-app/
│
├── README.md
├── .gitignore
├── docker-compose.yml              # (Optional) Run Rails + Python together
│
├── docs/
│   ├── architecture.png            # System architecture diagram
│   ├── api-examples.md              # Sample API requests & responses
│   └── agent-flow.md                # Agent reasoning explanation
│
├── rails-api/                       # Rails API Gateway
│   ├── Gemfile
│   ├── Gemfile.lock
│   ├── config/
│   │   ├── routes.rb
│   │   ├── application.rb
│   │   └── credentials.yml.enc
│   │
│   ├── app/
│   │   ├── controllers/
│   │   │   └── api/
│   │   │       └── v1/
│   │   │           └── questions_controller.rb
│   │   │
│   │   ├── services/
│   │   │   ├── shopify/
│   │   │   │   ├── oauth_service.rb
│   │   │   │   ├── graphql_client.rb
│   │   │   │   └── token_store.rb
│   │   │   │
│   │   │   └── python_ai_client.rb
│   │   │
│   │   └── models/
│   │       └── store.rb             # (Optional) Persist store metadata
│   │
│   ├── db/
│   │   ├── migrate/
│   │   └── schema.rb
│   │
│   └── spec/                        # (Optional) RSpec tests
│
├── python-ai-service/               # AI & Analytics Engine
│   ├── requirements.txt
│   ├── main.py                      # FastAPI entry point
│   │
│   ├── app/
│   │   ├── api/
│   │   │   └── analyze.py            # /analyze endpoint
│   │   │
│   │   ├── agent/
│   │   │   ├── agent.py              # Orchestrates workflow
│   │   │   ├── intent_classifier.py
│   │   │   ├── planner.py
│   │   │   ├── shopifyql_generator.py
│   │   │   ├── validator.py
│   │   │   └── explainer.py
│   │   │
│   │   ├── llm/
│   │   │   ├── prompt_templates.py
│   │   │   └── llm_client.py
│   │   │
│   │   ├── shopify/
│   │   │   ├── client.py              # Shopify Admin API client
│   │   │   └── query_executor.py
│   │   │
│   │   └── utils/
│   │       ├── logger.py
│   │       └── time_helpers.py
│   │
│   └── tests/
│       └── test_agent.py
│
└── scripts/
    ├── seed_mock_data.py             # Mock Shopify data (if no real store)
    └── run_local.sh
