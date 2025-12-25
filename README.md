# iFlow 技能系统发布包

## 📦 发布包概述

本发布包包含 iFlow 系统的核心技能模块，实现记忆管理、任务协调、命令处理、记忆共享和远程控制等完整功能。

### 🎯 核心功能模块

1. **记忆系统技能** - 智能记忆管理和存储
2. **任务分解调配技能** - 多Agent任务协调和分配
3. **命令技能** - 技能加载和系统命令处理
4. **记忆共享技能** - 跨主机记忆同步和共享
5. **远程控制技能** - 远程iFlow节点控制和管理

---

## 🧠 记忆系统技能

### 功能描述
提供完整的记忆管理功能，包括记忆存储、检索、智能搜索和情感记忆处理。

### 核心文件
```
skills/memory-system/
├── memory_manager.py              # 记忆管理器核心
├── intelligent_memory_system.py   # 智能记忆系统
├── integrated_memory_system.py    # 集成记忆系统
├── memory_recall.py               # 记忆召回功能
├── soulful_memory.py              # 情感记忆处理
├── smart_memory_search.py         # 智能记忆搜索
├── memory_mcp_client.py           # MCP客户端
├── memory_mcp_server.py           # MCP服务器
├── memory_system-backup/          # 备份记忆系统
│   ├── assets/
│   │   └── config.json
│   └── scripts/
│       ├── memory_skill.py
│       └── memory_backup.py
└── shared-memory-system/          # 共享记忆系统
    ├── assets/
    │   └── config.json
    └── scripts/
        ├── memory_skill.py
        ├── memory_client.py
        ├── memory_server.py
        ├── shared_memory_manager.py
        └── memory_sync.py
```

### 使用方法

#### 基础记忆操作
```python
from memory_manager import MemoryManager

# 创建记忆管理器
manager = MemoryManager()

# 存储记忆
result = manager.store_memory(
    key="important_info",
    value="重要信息内容",
    category="general",
    metadata={"importance": "high"}
)

# 检索记忆
memory = manager.retrieve_memory("important_info")

# 搜索记忆
results = manager.search_memories("重要信息")
```

#### 智能记忆处理
```python
from soulful_memory import process_conversation_with_soul

# 情感记忆处理
conversation = "用户对话内容..."
result = process_conversation_with_soul(conversation)
```

#### 记忆搜索
```python
from smart_memory_search import SmartMemorySearch

searcher = SmartMemorySearch()
results = searcher.search("查询关键词", category="user_preference")
```

### 配置文件
- `user_memories.json` - 用户记忆数据
- `iflow_memory_config.json` - 记忆系统配置

---

## 🎯 任务分解调配技能

### 功能描述
实现多Agent任务协调、智能任务分解、跨主机任务分配和结果聚合。

### 核心文件
```
skills/task-coordinator/
├── task_coordinator.py            # 任务协调器核心
├── agent_host_assignment_manager.py # Agent主机分配管理器
├── remote_iflow_executor.py       # 远程iFlow执行器
├── agent_host_assignment.json     # 主机分配配置
└── scripts/                       # 任务协调脚本
    ├── task_coordinator.py
    ├── task_decomposer.py
    ├── agent_matcher.py
    ├── result_aggregator.py
    ├── file_sync_system.py
    ├── hybrid_task_decomposer.py
    ├── intelligent_task_decomposer.py
    └── session_manager.py
```

### 核心功能
1. **任务分解** - 智能分解复杂任务
2. **Agent匹配** - 基于能力匹配最优Agent
3. **并行执行** - 多Agent并行任务处理
4. **结果聚合** - 智能结果合并和冲突解决
5. **跨主机协调** - 支持多主机任务分配

### 使用方法

#### 任务协调器
```python
from agent_host_assignment_manager import AgentHostAssignmentManager

# 创建任务管理器
manager = AgentHostAssignmentManager()

# 单Agent任务
result = manager.execute_agent_task(
    agent_id="xiaozhang_agent",
    task_config={
        "task": "市场分析",
        "parameters": {...}
    }
)

# 多Agent并行任务
task_assignments = [
    {"agent_id": "xiaozhang_agent", "task_config": {...}},
    {"agent_id": "xiaoli_agent", "task_config": {...}}
]
results = manager.execute_parallel_tasks(task_assignments)
```

#### 任务分解
```python
from task_coordinator import TaskCoordinator

coordinator = TaskCoordinator()
decomposed_tasks = coordinator.decompose_task("复杂任务描述")
```

### 配置说明
`agent_host_assignment.json` 配置格式：
```json
{
  "hosts": [
    {
      "name": "144主机",
      "ip": "192.168.31.144",
      "user": "林浩",
      "role": "primary",
      "assigned_agents": ["xiaozhang_agent", "xiaoli_agent"]
    }
  ],
  "assignment_strategy": "fixed_host_assignment",
  "load_balancing": true
}
```

---

## ⚡ 命令技能

### 功能描述
提供技能快速加载、系统启动、命令处理和性能优化功能。

### 核心文件
```
skills/command-skills/
├── load_skills_quick.py           # 快速技能加载器
├── quick_skills_loader.py         # 快速加载器核心
├── skills_manager.py              # 技能管理器
├── skills_launcher.py             # 技能启动器
├── iflow_startup.py               # iFlow启动脚本
└── iflow_complete_startup.py      # 完整启动脚本
```

### 使用方法

#### 快速技能加载
```bash
# 快速加载所有技能
python3 load_skills_quick.py

# 强制重新加载
python3 load_skills_quick.py reload

# 查看缓存状态
python3 load_skills_quick.py status

# 清理缓存
python3 load_skills_quick.py clear
```

#### 技能管理
```python
from skills_manager import SkillsManager

manager = SkillsManager()
result = manager.auto_load_all_skills()
```

#### 系统启动
```bash
# 基础启动
python3 iflow_startup.py

# 完整启动
python3 iflow_complete_startup.py
```

### 性能优化
- 智能缓存机制，性能提升55.3%
- 并行加载，充分利用多核CPU
- 自动缓存失效，确保数据新鲜度

---

## 🔄 记忆共享技能

### 功能描述
实现跨主机记忆同步、MCP协议通信、分布式记忆管理。

### 核心文件
```
skills/shared-memory/
├── memory_mcp_client.py           # MCP客户端
├── memory_mcp_server.py           # MCP服务器
├── shared_memory_client.py        # 共享内存客户端
├── setup_shared_memory.py         # 共享内存设置
├── skills_memory_client.py        # 技能记忆客户端
├── skills_memory_server.py        # 技能记忆服务器
├── skills_memory_receiver.py      # 记忆接收器
└── shared-memory-system/          # 共享记忆系统模块
    ├── assets/config.json
    └── scripts/
        ├── memory_skill.py
        ├── memory_client.py
        ├── memory_server.py
        ├── shared_memory_manager.py
        └── memory_sync.py
```

### 使用方法

#### MCP客户端
```python
from memory_mcp_client import MemoryMCPClient

client = MemoryMCPClient()
result = client.store_memory("key", "value", "category")
```

#### 共享内存设置
```bash
python3 setup_shared_memory.py
```

#### 记忆同步
```python
from skills_memory_server import SkillsMemoryServer

server = SkillsMemoryServer()
server.sync_memory()
```

---

## 🌐 远程控制技能

### 功能描述
提供远程iFlow节点控制、SSH连接管理、子Agent协调功能。

### 核心文件
```
skills/remote-control/
├── subagent-manager/              # 子Agent管理系统
│   ├── assets/
│   │   └── config.json
│   └── scripts/
│       ├── subagent_manager.py
│       ├── remote_session_manager.py
│       └── agent_coordinator.py
├── ssh_test.py                    # SSH连接测试
└── remote_host_connector.py       # 远程主机连接器
```

### 使用方法

#### 子Agent管理
```python
from subagent_manager import SubAgentManager

manager = SubAgentManager()
result = manager.manage_remote_agent("agent_id", "host_ip")
```

#### SSH连接测试
```bash
python3 ssh_test.py
```

#### 远程主机连接
```python
from remote_host_connector import RemoteHostConnector

connector = RemoteHostConnector()
result = connector.connect_to_host("192.168.31.144", "username")
```

---

## 📁 文件结构总览

```
发布/
├── skills/                        # 技能模块
│   ├── memory-system/            # 记忆系统技能
│   ├── task-coordinator/         # 任务协调技能
│   ├── command-skills/           # 命令技能
│   ├── shared-memory/            # 记忆共享技能
│   └── remote-control/           # 远程控制技能
├── frontend/                     # 前端界面（预留）
├── backend/                      # 后端服务（预留）
├── docs/                         # 文档目录
├── config/                       # 配置文件
│   ├── user_memories.json
│   ├── user_preferences.json
│   ├── iflow_memory_config.json
│   └── agent_host_assignment.json
└── examples/                     # 示例代码
```

---

## 🚀 快速开始

### 1. 环境准备
```bash
# 确保Python 3.9+环境
python3 --version

# 安装依赖（如有）
pip3 install -r requirements.txt
```

### 2. 配置设置
```bash
# 复制配置文件
cp config/*.json ~/.iflow/

# 编辑主机配置
vim config/agent_host_assignment.json
```

### 3. 启动系统
```bash
# 快速加载技能
cd skills/command-skills
python3 load_skills_quick.py

# 启动记忆系统
cd ../memory-system
python3 memory_manager.py

# 启动任务协调器
cd ../task-coordinator
python3 task_coordinator.py
```

### 4. 验证功能
```bash
# 测试记忆功能
python3 -c "from memory_manager import MemoryManager; MemoryManager().store_memory('test', '测试记忆')"

# 测试任务协调
python3 -c "from agent_host_assignment_manager import AgentHostAssignmentManager; print(AgentHostAssignmentManager().get_assignment_summary())"
```

---

## 📖 详细使用指南

### 记忆系统完整流程
1. **初始化记忆管理器**
2. **存储用户交互记忆**
3. **智能记忆搜索和召回**
4. **情感记忆处理**
5. **跨主机记忆同步**

### 任务协调完整流程
1. **任务接收和分析**
2. **智能任务分解**
3. **Agent能力匹配**
4. **任务分配和执行**
5. **结果收集和聚合**
6. **冲突解决和输出**

### 远程控制完整流程
1. **主机连接配置**
2. **SSH连接建立**
3. **远程Agent管理**
4. **任务分发和监控**
5. **结果回收和同步**

---

## 🔧 配置详解

### 主机分配配置
支持多主机Agent分配，包括：
- 主机信息和连接参数
- Agent能力配置
- 负载均衡策略
- 故障转移机制

### 记忆系统配置
包括：
- 记忆存储路径
- 缓存策略
- 同步设置
- 搜索索引配置

### 任务协调配置
包括：
- 任务分解策略
- Agent匹配算法
- 并发控制参数
- 结果聚合规则

---

## 🛠️ 故障排除

### 常见问题
1. **技能加载失败** → 检查配置文件格式
2. **记忆存储异常** → 验证文件权限和磁盘空间
3. **远程连接失败** → 检查SSH配置和网络连通性
4. **任务分配异常** → 验证Agent状态和主机配置

### 调试方法
```bash
# 查看详细日志
python3 load_skills_quick.py status

# 测试网络连接
python3 ssh_test.py

# 验证配置文件
python3 -c "import json; print(json.load(open('config/agent_host_assignment.json')))"
```

---

## 📈 性能优化

### 记忆系统优化
- 使用LRU缓存减少IO操作
- 异步记忆处理提升响应速度
- 智能索引优化搜索性能

### 任务协调优化
- 并行任务执行提升效率
- 智能负载均衡优化资源利用
- 缓存Agent状态减少查询开销

### 远程控制优化
- 连接池复用减少建连开销
- 压缩传输减少网络带宽
- 异步操作提升并发性能

---

## 🔮 未来扩展

1. **Web管理界面** - 提供图形化管理界面
2. **API服务** - RESTful API支持
3. **插件系统** - 支持第三方插件扩展
4. **监控告警** - 系统状态监控和告警
5. **容器化部署** - Docker容器化支持

---

## 📞 技术支持

- **文档版本**: 1.0.0
- **发布日期**: 2025-12-25
- **维护团队**: maihh
- **技术支持**: 通过GitHub Issues或内部渠道

---

**注意**: 本发布包包含完整的iFlow技能系统，请根据实际需求选择相应模块进行部署和使用。
