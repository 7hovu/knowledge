```python
from pyscipopt import Model

# 创建一个模型
model = Model("Simple LP")

# 添加变量
x = model.addVar("x", vtype="CONTINUOUS", lb=0)
y = model.addVar("y", vtype="CONTINUOUS", lb=0)

# 添加约束
model.addCons(2*x + y <= 10)
model.addCons(x + 3*y <= 12)

# 设置目标函数 (最大化)
model.setObjective(3*x + 4*y, "maximize")

# 求解模型
model.optimize()

# 检查求解状态
if model.getStatus() == "optimal":
    print("找到最优解！")
    print(f"目标值: {model.getObjVal()}")
    print(f"x = {model.getVal(x)}")
    print(f"y = {model.getVal(y)}")
else:
    print(f"求解结束，状态为: {model.getStatus()}")


```
