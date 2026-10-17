# 🎯 Schema Managers - Cost Optimization Solutions

This directory contains **6 different schema management approaches** to solve the 50,000 token schema problem. Each approach reduces LLM costs by intelligently selecting only relevant schema parts.

## The Problem

**Before**: 50,000 tokens × $0.15/1M = **$0.0075 per query**
**After**: 5,000 tokens × $0.15/1M = **$0.00075 per query**
**Savings**: **90% cost reduction** 🎉

## Solution Overview

### 1. **Schema Chunking & Intelligent Selection** (`schema_chunking.py`)
- **Approach**: Extracts entities from queries and selects only relevant tables
- **Best For**: General queries with clear entity mentions
- **Token Reduction**: 50K → 5K (90% reduction)


### 2. **Hierarchical Schema Representation** (`hierarchical_schema.py`)
- **Approach**: Provides 3 levels of schema detail (basic, detailed, full)
- **Best For**: Queries with varying complexity requirements
- **Token Reduction**: 50K → 1K-15K (70-98% reduction)


### 3. **Query Intent Classification** (`intent_based_schema.py`)
- **Approach**: Classifies query intent and fetches domain-specific tables
- **Best For**: Domain-specific queries (Medicaid URA, ecommerce, healthcare)
- **Token Reduction**: 50K → 2K-8K (84-96% reduction)


### 4. **Schema Embeddings + Vector Search** (`vector_schema.py`)
- **Approach**: Uses semantic similarity to find relevant schema chunks
- **Best For**: Complex queries requiring semantic understanding
- **Token Reduction**: 50K → 3K-10K (80-94% reduction)


### 5. **Progressive Schema Loading** (`progressive_schema.py`)
- **Approach**: Loads schema progressively based on query complexity
- **Best For**: Adaptive systems that learn from usage patterns
- **Token Reduction**: 50K → 1K-10K (80-98% reduction)


### 6. **🆕 LLM Dynamic Schema Manager** (`llm_dynamic_schema.py`)
- **Approach**: Uses LLMs to dynamically analyze domains and adapt schema selection
- **Best For**: **Any domain** - automatically adapts to healthcare, ecommerce, finance, etc.
- **Token Reduction**: 50K → 2K-8K (84-96% reduction)

- **🔥 NEW**: **Domain-agnostic** - works with any business domain!

## 🚀 Quick Start

### 1. **Install Dependencies**
```bash
pip install -r requirements.txt
```

### 2. **Configure LLM Providers** (for dynamic schema manager)
```bash
# Copy and configure environment variables
cp env.example .env

# Add your API keys
OPENAI_API_KEY=your_openai_key
ANTHROPIC_API_KEY=your_anthropic_key
```

### 3. **Test Individual Managers**
```bash
# Test all managers
python test_schema_managers.py

# Test specific manager
python -c "
from schema_managers.llm_dynamic_schema import LLMDynamicSchemaManager
manager = LLMDynamicSchemaManager()
print('✅ LLM Dynamic Schema Manager ready!')
"
```

### 4. **Use Integrated Approach**
```bash
python integrate_schema_managers.py
```

## 🌍 **Multi-Domain Support**

The **LLM Dynamic Schema Manager** automatically adapts to any business domain:

### **Healthcare/Medicaid**
```python
queries = [
    "Find URA discrepancies in drug pricing",
    "Analyze CPI penalty adjustments",
    "Compare AMP vs BP across manufacturers"
]
# Automatically selects: DRUGS, PRICING, REBATES, MANUFACTURERS tables
```

### **E-commerce**
```python
queries = [
    "Analyze customer purchase patterns",
    "Find products with low inventory",
    "Compare sales across regions"
]
# Automatically selects: CUSTOMERS, ORDERS, PRODUCTS, INVENTORY tables
```

### **Finance**
```python
queries = [
    "Find suspicious transaction patterns",
    "Analyze account balance trends",
    "Compare revenue across quarters"
]
# Automatically selects: TRANSACTIONS, ACCOUNTS, BALANCES, REVENUE tables
```

### **Manufacturing**
```python
queries = [
    "Analyze production line efficiency",
    "Find quality control issues",
    "Compare supplier performance"
]
# Automatically selects: PRODUCTION, QUALITY, SUPPLIERS, INVENTORY tables
```

## 🎯 **For Your Medicaid URA Use Case**

The **LLM Dynamic Manager** is now the **recommended choice**:
- **Automatically recognizes** Medicaid, URA, rebate, AMP, BP, CPI, NDC keywords
- **No hardcoding** - learns from your data and queries
- **Adapts to changes** in your business domain
- **Maintains performance** while being completely flexible

```python
from schema_managers.llm_dynamic_schema import LLMDynamicSchemaManager, LLMProvider

manager = LLMDynamicSchemaManager(
    llm_provider=LLMProvider.ANTHROPIC,  # or OPENAI
    max_tokens_per_query=5000
)

# Works with any domain automatically
result = manager.get_adaptive_schema(
    "Find URA discrepancies in Q1 2024",
    available_tables, 
    full_schema
)

print(f"Domain: {result['metadata']['domain']}")
print(f"Intent: {result['metadata']['query_intent']['intent']}")
print(f"Tables: {result['metadata']['selected_tables']}")
```

## 🔧 Integration with Your Deep Agent

### **Option 1: Use LLM Dynamic Manager (Recommended)**
```python
from schema_managers.llm_dynamic_schema import LLMDynamicSchemaManager

class QueryAgent(BaseAgent):
    def __init__(self):
        super().__init__("Query")
        self.schema_manager = LLMDynamicSchemaManager()
    
    def select_relevant_tables(self, query: str) -> List[str]:
        result = self.schema_manager.get_adaptive_schema(
            query, self.available_tables, self.full_schema
        )
        return result["metadata"]["selected_tables"]
```

### **Option 2: Use Orchestrator for Best Performance**
```python
from schema_managers.integrate_schema_managers import SchemaManagerOrchestrator

orchestrator = SchemaManagerOrchestrator()

# Automatically selects best manager for each query
result = orchestrator.get_optimal_schema(
    user_query="Find URA discrepancies",
    available_tables=available_tables,
    full_schema=full_schema,
    max_tokens=5000
)

print(f"Selected manager: {result['metadata']['selected_manager']}")
print(f"Domain: {result['metadata'].get('domain', 'unknown')}")
```

## 📈 Cost Analysis

### **Monthly Costs (1000 queries)**
- **Before Optimization**: $7.50
- **After Optimization**: $0.75
- **Annual Savings**: $81.00

### **Token Usage Comparison**
```
Original Schema: 50,000 tokens
├── Chunking: 5,000 tokens (90% reduction)
├── Hierarchical: 1,000-15,000 tokens (70-98% reduction)
├── Intent-Based: 2,000-8,000 tokens (84-96% reduction)
├── Vector: 3,000-10,000 tokens (80-94% reduction)
├── Progressive: 1,000-10,000 tokens (80-98% reduction)
└── 🆕 LLM Dynamic: 2,000-8,000 tokens (84-96% reduction)
```

## 🧪 Testing

### **Run All Tests**
```bash
python test_schema_managers.py
```

### **Test LLM Dynamic Manager**
```python
from test_schema_managers import create_mock_schema, test_llm_dynamic_schema_manager

mock_schema = create_mock_schema()
result = test_llm_dynamic_schema_manager(mock_schema)
print(f"Status: {result['status']}")
```

### **Performance Testing**
```python
# Test with different domains
test_queries = [
    "How many drugs are in the DRUGS table?",  # Healthcare
    "Analyze customer data for marketing campaigns",  # E-commerce
    "Find financial transaction patterns",  # Finance
    "Compare different business domains"  # Generic
]

for query in test_queries:
    start_time = time.time()
    result = manager.get_adaptive_schema(query, tables, schema)
    execution_time = time.time() - start_time
    
    print(f"Query: {query[:50]}...")
    print(f"Domain: {result['metadata']['domain']}")
    print(f"Time: {execution_time:.4f}s")
    print(f"Tables: {len(result['metadata']['selected_tables'])}")
    print()
```

## 🔍 Monitoring and Optimization

### **Performance Metrics**
```python
# Get performance summary
performance = orchestrator.get_manager_performance_summary()
for manager, metrics in performance.items():
    print(f"{manager}:")
    print(f"  Avg Time: {metrics['average_execution_time']:.4f}s")
    print(f"  Avg Score: {metrics['average_performance_score']:.2f}")
    print(f"  Total Queries: {metrics['total_queries']}")
```

### **Domain Analysis**
```python
# Check domain understanding
result = manager.get_adaptive_schema(query, tables, schema)
domain_context = result['metadata']['domain_analysis']

print(f"Domain: {domain_context.domain}")
print(f"Keywords: {domain_context.keywords}")
print(f"Core Concepts: {domain_context.core_concepts}")
print(f"Business Entities: {domain_context.business_entities}")
```

## 🚨 Troubleshooting

### **Common Issues**

1. **Import Errors**
   ```bash
   pip install oracledb tiktoken sentence-transformers scikit-learn openai anthropic
   ```

2. **LLM API Key Issues**
   ```bash
   # Check your .env file
   OPENAI_API_KEY=your_key_here
   ANTHROPIC_API_KEY=your_key_here
   ```

3. **Memory Issues**
   ```python
   # Reduce chunk size
   manager = LLMDynamicSchemaManager(max_tokens_per_query=3000)
   ```

4. **Performance Issues**
   ```python
   # Clear caches
   manager.clear_cache()
   ```

### **Fallback Strategy**
```python
try:
    result = manager.get_adaptive_schema(query, tables, schema)
except Exception as e:
    logger.warning(f"LLM manager failed: {e}, using fallback")
    result = get_fallback_schema(query, tables[:3], schema)
```

## 🔮 Future Enhancements

- **Multi-LLM Ensemble**: Combine multiple LLM providers for better accuracy
- **Domain-Specific Fine-tuning**: Train models on your specific business domain
- **Real-time Learning**: Learn from user feedback and query patterns
- **Hybrid Approaches**: Combine LLM analysis with traditional methods
- **Cost Optimization**: Dynamic token allocation based on query importance

## 📚 Additional Resources

- **Main README**: `../README.md`
- **Test Scripts**: `test_schema_managers.py`
- **Integration**: `integrate_schema_managers.py`
- **Configuration**: `../config.py`
- **Environment**: `../env.example`

## 🤝 Contributing

1. Test your changes with `python test_schema_managers.py`
2. Ensure token reduction is maintained
3. Add performance metrics for new approaches
4. Update this README with new features
5. Test with different domains to ensure adaptability

---

**🎯 Goal**: Reduce schema token usage from 50,000 to 5,000 tokens (90% reduction)
**💰 Result**: Annual savings of $81.00 for 12,000 queries
**🚀 Impact**: Scalable, cost-effective deep agent system
**🌍 Bonus**: **Domain-agnostic** - works with any business domain automatically! 
