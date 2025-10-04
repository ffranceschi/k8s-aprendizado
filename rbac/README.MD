# RBAC (Role-Based Access Control) 

# Role e ClusterRole 

# RoleBinding vinculo do Role a um usuário ou grupo de usuários.
# ClusterRoleBinding vinculo do ClusterRole a um usuário ou grupo de usuários.

# depois de rodar o kubeboard.yaml
k get clusterrole | grep full-access

# Conceito de vincular o clusterRole é igual ao role, porém precisa do namespace.
