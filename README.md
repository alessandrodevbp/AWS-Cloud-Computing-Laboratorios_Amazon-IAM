<p align="center">
  <img width="767" height="385" alt="Image" src="https://github.com/user-attachments/assets/b3162a5d-a10d-457d-91be-19a471308334" />
</p>

# 🔐 AWS — Introdução ao AWS Identity and Access Management (IAM)

## 📌 Sobre o laboratório

Este laboratório apresenta o **AWS Identity and Access Management (IAM)**, serviço utilizado para gerenciar usuários, grupos, credenciais e permissões de acesso aos recursos da AWS.

Durante a atividade, foram explorados usuários e grupos de usuários pré-criados, políticas de permissões e os efeitos dessas políticas sobre o acesso aos serviços **Amazon S3** e **Amazon EC2**.

---

## 🎯 Objetivos

Ao concluir este laboratório, os principais objetivos foram:

* 🔑 Criar e aplicar uma política de senhas do IAM;
* 👤 Explorar usuários e grupos de usuários pré-criados;
* 📜 Inspecionar as políticas do IAM aplicadas aos grupos;
* 👥 Adicionar usuários a grupos com capacidades específicas;
* 🔗 Localizar e utilizar o URL de login do IAM;
* 🧪 Testar os efeitos das políticas sobre o acesso aos serviços da AWS.

---

## 🔐 AWS Identity and Access Management (IAM)

O **IAM** permite gerenciar usuários e controlar as operações que cada identidade pode realizar na AWS.

Entre suas funcionalidades estão:

* Gerenciamento de usuários do IAM e suas credenciais;
* Gerenciamento de funções e permissões;
* Gerenciamento de usuários federados e suas permissões.

O laboratório teve duração aproximada de **60 minutos**.

---

## 🛠️ Configuração utilizada

### 🔑 Política de senhas

Foi criada uma política de senhas personalizada para a conta AWS com os seguintes requisitos:

| Configuração                   | Valor            |
| ------------------------------ | ---------------- |
| Comprimento mínimo             | 10 caracteres    |
| Requisitos de senha            | Ativados         |
| Expiração da senha             | 90 dias          |
| Reutilização de senhas         | Últimas 5 senhas |
| Redefinição pelo administrador | Desabilitada     |

As alterações foram aplicadas no nível da conta e passaram a afetar os usuários associados à conta.

---

## 👥 Usuários e grupos

O laboratório disponibilizou três usuários:

* 👤 `user-1`
* 👤 `user-2`
* 👤 `user-3`

Também foram disponibilizados três grupos:

* 📦 `S3-Support`
* 💻 `EC2-Support`
* 🔐 `EC2-Admin`

---

## 📜 Políticas e permissões

Durante o laboratório foram analisadas diferentes políticas de acesso.

### 📦 S3-Support

O grupo possui a política:

`AmazonS3ReadOnlyAccess`

Essa política permite obter e listar recursos do **Amazon S3**.

### 💻 EC2-Support

O grupo possui a política:

`AmazonEC2ReadOnlyAccess`

Essa política permite visualizar informações relacionadas ao **Amazon EC2**, **Elastic Load Balancing**, **Amazon CloudWatch** e **Amazon EC2 Auto Scaling**, sem permitir modificações nesses recursos.

### 🔐 EC2-Admin

O grupo possui uma política inline:

`EC2-Admin-Policy`

Essa política permite visualizar informações do Amazon EC2 e **iniciar e interromper instâncias**.

---

## 👥 Associação dos usuários aos grupos

Os usuários foram associados aos grupos de acordo com suas funções:

| Usuário     | Grupo         | Permissões                                       |
| ----------- | ------------- | ------------------------------------------------ |
| 👤 `user-1` | `S3-Support`  | Somente leitura no Amazon S3                     |
| 👤 `user-2` | `EC2-Support` | Somente leitura no Amazon EC2                    |
| 👤 `user-3` | `EC2-Admin`   | Visualizar, iniciar e interromper instâncias EC2 |

Essa configuração demonstra como as permissões podem ser atribuídas por meio de grupos, permitindo organizar o acesso de acordo com a função de cada usuário.

---

## 🧪 Testes de acesso

Após a associação dos usuários aos grupos, foram realizados testes utilizando o **URL de login dos usuários do IAM**.

### 👤 user-1 — S3 Support

O `user-1` conseguiu acessar o **Amazon S3** e visualizar os buckets e seus conteúdos.

Ao tentar acessar o **Amazon EC2**, o usuário recebeu uma mensagem informando que não possuía autorização para realizar a operação.

**Resultado:**

* ✅ Amazon S3 — acesso permitido
* ❌ Amazon EC2 — acesso não autorizado

---

### 👤 user-2 — EC2 Support

O `user-2` conseguiu visualizar as instâncias do **Amazon EC2**, devido às permissões de somente leitura.

Ao tentar interromper uma instância, recebeu uma mensagem informando que não possuía autorização para realizar a operação.

Também não conseguiu listar os buckets do **Amazon S3**.

**Resultado:**

* ✅ Amazon EC2 — visualização permitida
* ❌ Amazon EC2 — alteração não permitida
* ❌ Amazon S3 — acesso não permitido

---

### 👤 user-3 — EC2 Admin

O `user-3`, associado ao grupo `EC2-Admin`, conseguiu visualizar as instâncias do Amazon EC2 e realizar a ação de **interromper uma instância**.

**Resultado:**

* ✅ Visualização de instâncias EC2
* ✅ Interrupção de instância EC2

---

## 📚 Principais aprendizados

Durante o laboratório, foram praticados conceitos importantes de **Identity and Access Management**, incluindo:

* 🔐 Gerenciamento de usuários;
* 👥 Gerenciamento de grupos;
* 📜 Políticas de permissões;
* 🔑 Política de senhas;
* 🛡️ Controle de acesso aos recursos;
* 📦 Permissões de somente leitura;
* ⚙️ Permissões para executar ações específicas;
* 🔗 Login utilizando usuários do IAM.

---

## 🧠 O que ficou de aprendizado

O principal aprendizado deste laboratório foi compreender como o **IAM controla o acesso aos recursos da AWS por meio de usuários, grupos e políticas**.

A atividade demonstrou, na prática, que usuários diferentes podem possuir níveis diferentes de acesso aos mesmos serviços.

O `user-1`, por exemplo, conseguiu acessar o Amazon S3, mas não o EC2. O `user-2` conseguiu visualizar recursos do EC2, porém não pôde modificá-los. Já o `user-3` possuía permissões suficientes para interromper uma instância EC2.

---

## 📸 Evidências do laboratório

### 🔐 Política de senhas

<p align="center">
  <img width="1920" height="888" alt="Image" src="https://github.com/user-attachments/assets/dad83b81-8c9e-4cec-b481-da349e1cedf4" />
</p>

---

## 🧰 Tecnologias e serviços

![AWS](https://img.shields.io/badge/AWS-Cloud-orange?style=for-the-badge&logo=amazonaws)

![IAM](https://img.shields.io/badge/AWS-IAM-orange?style=for-the-badge&logo=amazonaws)

![S3](https://img.shields.io/badge/Amazon-S3-orange?style=for-the-badge&logo=amazons3)

![EC2](https://img.shields.io/badge/Amazon-EC2-orange?style=for-the-badge&logo=amazonec2)

**Serviços e conceitos estudados:**

`AWS IAM` • `IAM Users` • `IAM Groups` • `IAM Policies` • `Password Policy` • `Amazon S3` • `Amazon EC2` • `Managed Policies` • `Inline Policies` • `Permissions`


---

## 📖 Referência

**AWS Training and Certification**

Laboratório: **Introdução ao AWS Identity and Access Management (IAM)**.

Material utilizado para a realização das atividades práticas deste laboratório.

---

## 🚀 Próximos passos

🔹 Continuar os laboratórios práticos de **AWS Cloud**;

🔹 Aprofundar os estudos em **IAM, políticas e controle de acesso**;

🔹 Avançar para outros serviços da AWS;

🔹 Continuar desenvolvendo experiência prática por meio de laboratórios e projetos.

---

<p align="center">
  <sub>☁️ Laboratório prático de AWS Cloud desenvolvido para fins educacionais e de aprendizado contínuo.</sub>
</p>

<p align="center">
  <sub>© 2026 Alessandrodevbp — Todos os direitos reservados.</sub>
</p>





<p align="center">
  <sub>© 2026 Alessandro Batista Prudente — Todos os direitos reservados.</sub>
</p>
