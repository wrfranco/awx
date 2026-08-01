Uso do playbook ping_host.yml

Este playbook faz um `ping` no host passado via variável `target_host`. O host deve existir no Inventory do AWX.

Exemplos de uso:

1) No AWX (via Job Template)
- Crie/edite um Job Template apontando para o projeto/branch que contém `playbooks/ping_host.yml`.
- Em `Inventory` selecione o inventário que contém o host alvo.
- Em `Credentials` selecione as credenciais apropriadas para conectar aos hosts.
- Em `Extra Variables` insira, por exemplo:

```
target_host: myserver.example.com
```

- Salve e clique em `Launch`.

2) Local (linha de comando)
- Supondo que você tenha um `inventory` com o host definido:

```bash
ansible-playbook -i inventory playbooks/ping_host.yml -e "target_host=myserver.example.com"
```

Observações:
- `target_host` precisa corresponder exatamente a um host definido no inventário (ou a um pattern que o selecione).
- Se quiser pingar um host que não está no inventário, considere adicionar dinamicamente com `add_host` ou criar um inventório com `host_vars` apropriados.
