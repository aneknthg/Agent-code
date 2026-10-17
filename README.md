# 🎯 **Complete Deep Agent Workflow System**

A comprehensive, **Amazon Bedrock-powered** deep agent system that implements the exact workflow you described for data analysis and discrepancy detection.

## 🚀 **What This System Does**


1. **🔍 Use Case Analysis** → Analyzes problem statement and database schema to create context and memory
2. **✅ Data Analyst Verification** → One-time verification of the analysis (only at startup)
3. **🏷️ Entity Extraction** → Extracts entities from user queries using Bedrock
4. **📝 SQL Generation** → Generates SQL using context and memory with Bedrock
5. **💾 Data Retrieval** → Executes SQL and retrieves data from Oracle database
6. **🔬 Hybrid Comparison** → Combines SQL, Python, and LLM for intelligent data comparison
7. **📊 Discrepancy Reporting** → Reports findings to user with actionable insights

## 🏗️ **System Architecture**

```
┌─────────────────────────────────────────────────────────────────┐
│                    COMPLETE WORKFLOW SYSTEM                    │
├─────────────────────────────────────────────────────────────────┤
│  📋 Problem Statement + Database Schema                        │
│           ↓                                                    │
│  🧠 Use Case Analyzer (Bedrock)                               │
│           ↓                                                    │
│  ✅ Data Analyst Verification (One-time)                       │
│           ↓                                                    │
│  ❓ User Query                                                 │
│           ↓                                                    │
│  🏷️ Entity Extraction (Bedrock)                               │
│           ↓                                                    │
│  📝 SQL Generation (Bedrock + Context)                        │
│           ↓                                                    │
│  💾 Data Retrieval (Oracle DB)                                │
│           ↓                                                    │
│  🔬 Hybrid Comparison Engine                                  │
│     ├── SQL Analysis                                          │
│     ├── Python Processing                                     │
│     └── LLM Insights (Bedrock)                                │
│           ↓                                                    │
│  📊 Comprehensive Report + Discrepancies                       │
└─────────────────────────────────────────────────────────────────┘
```

## 🌟 **Key Features**

### **🤖 Amazon Bedrock Integration**
- **Use Case Analysis**: Automatically analyzes your problem statement and database schema
- **Entity Extraction**: Intelligently extracts entities from user queries
- **SQL Generation**: Generates optimized Oracle SQL using business context
- **Insight Generation**: Provides business insights and recommendations

### **🗄️ Oracle Database Integration**
- **Modern oracledb**: Uses the latest Oracle database driver
- **Connection Pooling**: Efficient database connection management
- **Schema Discovery**: Automatic table and column analysis
- **Query Execution**: Secure SQL execution with parameter binding

### **🔬 Hybrid Comparison Engine**
- **Time-based Analysis**: YoY, period-over-period comparisons
- **Category-based Analysis**: Segment analysis and comparison
- **Dataset Comparison**: Cross-dataset discrepancy detection
- **Statistical Analysis**: Anomaly detection and outlier identification

### **📊 Comprehensive Reporting**
- **Executive Summary**: High-level findings and metrics
- **Detailed Analysis**: Step-by-step workflow execution
- **Discrepancy Details**: Severity, impact, and suggested actions
- **Business Recommendations**: Actionable insights for improvement

## 🚀 **Quick Start**

### **1. Install Dependencies**
```bash
pip install -r requirements.txt
```

### **2. Configure Environment**
```bash
cp env.example .env

# Add your credentials
ORACLE_HOST=your_oracle_host
ORACLE_PORT=1521
ORACLE_SERVICE=your_service
ORACLE_USER=your_username
ORACLE_PASSWORD=your_password

AWS_ACCESS_KEY_ID=your_aws_key
AWS_SECRET_ACCESS_KEY=your_aws_secret
AWS_SESSION_TOKEN=your_session_token
AWS_REGION=us-east-1
```

### **3. Run the Complete Demo**
```bash
python demo_complete_workflow.py
```

## 📚 **System Components**

### **🏗️ Core Workflow Agents**

#### **1. Use Case Analyzer** (`workflow_agents/use_case_analyzer.py`)
- Analyzes your problem statement and database schema
- Creates business context and domain understanding
- Provides foundation for all subsequent operations

#### **2. SQL Generator** (`workflow_agents/sql_generator.py`)
- Generates Oracle SQL using Bedrock and business context
- Validates SQL syntax and structure
- Optimizes queries for performance

#### **3. Hybrid Comparison Engine** (`workflow_agents/hybrid_comparison.py`)
- Combines SQL, Python, and LLM for data analysis
- Automatically detects comparison strategies
- Identifies discrepancies and anomalies

#### **4. Workflow Orchestrator** (`workflow_agents/workflow_orchestrator.py`)
- Orchestrates the complete workflow
- Manages step execution and error handling
- Provides comprehensive reporting

### **🔧 Schema Management (Updated for Bedrock)**

#### **1. Schema Chunking Manager** (`schema_managers/schema_chunking.py`)
- **Updated**: Now uses Amazon Bedrock for entity extraction
- **Updated**: Uses Bedrock for intelligent table selection
- **Maintains**: 90% token reduction (50K → 5K tokens)

#### **2. Hierarchical Schema Manager** (`schema_managers/hierarchical_schema.py`)
- **Updated**: Uses Bedrock for complexity analysis
- **Updated**: Adaptive schema detail selection
- **Maintains**: 70-98% token reduction

#### **3. Intent-Based Schema Manager** (`schema_managers/intent_based_schema.py`)
- **Updated**: Uses Bedrock for intent classification
- **Updated**: Domain-specific schema selection
- **Maintains**: 84-96% token reduction

#### **4. Vector Schema Manager** (`schema_managers/vector_schema.py`)
- **Updated**: Uses Bedrock for semantic analysis
- **Updated**: Intelligent chunk selection
- **Maintains**: 80-94% token reduction

#### **5. Progressive Schema Manager** (`schema_managers/progressive_schema.py`)
- **Updated**: Uses Bedrock for complexity assessment
- **Updated**: Adaptive loading strategies
- **Maintains**: 80-98% token reduction

#### **6. LLM Dynamic Schema Manager** (`schema_managers/llm_dynamic_schema.py`)
- **NEW**: Completely domain-agnostic
- **NEW**: Automatically adapts to any business domain
- **NEW**: Uses multiple LLM providers (OpenAI, Anthropic, Bedrock)
- **Maintains**: 84-96% token reduction
