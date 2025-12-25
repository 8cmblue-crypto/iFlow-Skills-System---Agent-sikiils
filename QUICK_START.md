# iFlow 技能系统 - 快速开始指南

## 🚀 5分钟快速部署

### 第一步：环境检查
```bash
# 检查Python版本
python3 --version  # 需要3.9+

# 检查网络连接（如果使用远程功能）
ping 192.168.31.144  # 测试到其他iFlow节点的连接
```

### 第二步：复制发布包
```bash
# 将发布文件夹复制到目标位置
cp -r /vol1/1000/iflow/发布 /your/target/path/
cd /your/target/path/发布
```

### 第三步：配置系统
```bash
# 复制配置文件到用户目录
mkdir -p ~/.iflow
cp config/* ~/.iflow/

# 编辑主机配置（根据实际情况修改）
vim ~/.iflow/agent_host_assignment.json
```

### 第四步：启动核心功能
```bash
# 1. 启动记忆系统
cd skills/memory-system
python3 memory_manager.py &

# 2. 加载技能（使用优化后的快速加载器）
cd ../command-skills
python3 load_skills_quick.py

# 3. 启动任务协调器（如果需要多Agent协作）
cd ../task-coordinator
python3 task_coordinator.py &
```

### 第五步：验证功能
```bash
# 测试记忆功能
python3 -c "
from memory_manager import MemoryManager
manager = MemoryManager()
result = manager.store_memory('test', 'iFlow技能系统启动成功', 'system')
print(f'记忆存储: {result[\"status\"]}')
"

# 测试任务协调（如果配置了多主机）
python3 -c "
from agent_host_assignment_manager import AgentHostAssignmentManager
manager = AgentHostAssignmentManager()
summary = manager.get_assignment_summary()
print(f'任务协调状态: {len(summary[\"hosts\"])} 个主机已配置')
"
```

## 📋 核心功能使用

### 🧠 记忆管理
```bash
# 存储记忆
python3 -c "
from memory_manager import MemoryManager
MemoryManager().store_memory('用户偏好', '用户喜欢使用快速加载器', 'preference')
"

# 搜索记忆
python3 -c "
from memory_manager import MemoryManager
results = MemoryManager().search_memories('用户偏好')
print(f'找到 {len(results)} 条相关记忆')
"

# 智能记忆处理
python3 -c "
from soulful_memory import process_conversation_with_soul
process_conversation_with_soul('用户今天学习了iFlow技能系统')
"
```

### ⚡ 技能快速加载
```bash
# 快速加载所有技能
python3 skills/command-skills/load_skills_quick.py

# 查看技能状态
python3 skills/command-skills/load_skills_quick.py status

# 重新加载（技能文件更新后）
python3 skills/command-skills/load_skills_quick.py reload
```

### 🎯 任务协调（多Agent）
```bash
# 查看Agent分配状态
python3 -c "
from agent_host_assignment_manager import AgentHostAssignmentManager
manager = AgentHostAssignmentManager()
print(manager.get_assignment_summary())
"

# 执行单Agent任务
python3 -c "
from agent_host_assignment_manager import AgentHostAssignmentManager
manager = AgentHostAssignmentManager()
result = manager.execute_agent_task('xiaozhang_agent', {
    'task': '市场分析',
    'parameters': {'target': '竞品分析'}
})
print(f'任务结果: {result}')
"
```

### 🔄 记忆共享（多主机）
```bash
# 启动记忆服务器
cd skills/shared-memory
python3 memory_mcp_server.py &

# 在其他主机上同步记忆
python3 -c "
from memory_mcp_client import MemoryMCPClient
client = MemoryMCPClient()
client.sync_memories()
"
```

### 🌐 远程控制
```bash
# 测试SSH连接
python3 skills/remote-control/ssh_test.py

# 连接远程主机
python3 -c "
from remote_host_connector import RemoteHostConnector
connector = RemoteHostConnector()
result = connector.connect_to_host('192.168.31.144', 'username')
print(f'连接结果: {result}')
"
```

## 🔧 常用配置

### 单机模式配置
```json
{
  "hosts": [
    {
      "name": "本地主机",
      "ip": "127.0.0.1",
      "user": "local",
      "role": "primary",
      "assigned_agents": ["local_agent"]
    }
  ],
  "assignment_strategy": "local_only",
  "load_balancing": false
}
```

### 双主机模式配置
```json
{
  "hosts": [
    {
      "name": "144主机",
      "ip": "192.168.31.144",
      "user": "林浩",
      "role": "primary",
      "assigned_agents": ["xiaozhang_agent", "xiaoli_agent"]
    },
    {
      "name": "77主机", 
      "ip": "192.168.31.77",
      "user": "linhao",
      "role": "secondary",
      "assigned_agents": ["xiaowang_agent", "xiaoliu_agent"]
    }
  ],
  "assignment_strategy": "fixed_host_assignment",
  "load_balancing": true
}
```

## 🛠️ 故障排除

### 问题1：技能加载失败
```bash
# 检查文件权限
ls -la skills/command-skills/

# 清理缓存重新加载
python3 skills/command-skills/load_skills_quick.py clear
python3 skills/command-skills/load_skills_quick.py reload
```

### 问题2：记忆存储异常
```bash
# 检查配置文件
python3 -c "import json; print(json.load(open('config/user_memories.json')))"

# 检查文件权限
ls -la ~/.iflow/
```

### 问题3：远程连接失败
```bash
# 测试SSH连接
ssh username@192.168.31.144 "echo 'SSH连接正常'"

# 检查网络连通性
ping 192.168.31.144
```

### 问题4：任务协调异常
```bash
# 检查Agent状态
python3 -c "
from agent_host_assignment_manager import AgentHostAssignmentManager
manager = AgentHostAssignmentManager()
for agent_id in ['xiaozhang_agent', 'xiaoli_agent']:
    agent = manager.get_agent_by_id(agent_id)
    print(f'{agent_id}: {agent}')
"
```

## 📈 性能监控

### 查看系统状态
```bash
# 记忆系统状态
python3 -c "
from memory_manager import MemoryManager
manager = MemoryManager()
print(f'总记忆数: {len(manager.memories)}')
"

# 技能加载性能
python3 skills/command-skills/load_skills_quick.py status

# 任务协调状态
python3 -c "
from agent_host_assignment_manager import AgentHostAssignmentManager
manager = AgentHostAssignmentManager()
print(manager.get_assignment_summary())
"
```

## 🎯 最佳实践

1. **日常使用**
   - 优先使用 `load_skills_quick.py` 加载技能
   - 定期检查记忆系统状态
   - 技能文件更新后及时重新加载

2. **多主机协作**
   - 确保主机间网络连通性
   - 配置好SSH免密登录
   - 定期同步记忆数据

3. **性能优化**
   - 使用缓存机制提升加载速度
   - 合理配置并发任务数量
   - 定期清理过期缓存文件

4. **故障预防**
   - 定期备份重要配置和记忆数据
   - 监控系统资源使用情况
   - 建立日志记录和告警机制

---

## 📞 获取帮助

如果遇到问题，请：
1. 查看详细文档：`发布/README.md`
2. 检查配置文件格式
3. 查看系统日志输出
4. 联系技术支持团队

**祝您使用愉快！** 🎉