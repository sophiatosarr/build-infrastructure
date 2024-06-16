# Build Infrastructure

### Passo a Passo

1. **Instalação do Terraform CLI:**
   - Abra o PowerShell como Administrador.
   - Baixe o Terraform executando o comando:
     ```shell
     Invoke-WebRequest -Uri https://releases.hashicorp.com/terraform/1.0.11/terraform_1.0.11_windows_amd64.zip -OutFile terraform.zip
     ```
   - Extraia o arquivo ZIP:
     ```shell
     Expand-Archive -Path terraform.zip -DestinationPath C:\terraform
     ```
   - Adicione o Terraform ao PATH do sistema:
     ```shell
     [System.Environment]::SetEnvironmentVariable('PATH', $env:PATH + ';C:\terraform', [System.EnvironmentVariableTarget]::Machine)
     ```
   - Verifique a instalação executando:
     ```shell
     terraform -v
     ```

2. **Instalação do AWS CLI:**
   - Abra o PowerShell como Administrador.
   - Baixe o instalador do AWS CLI executando:
     ```shell
     Invoke-WebRequest -Uri https://awscli.amazonaws.com/AWSCLIV2.msi -OutFile AWSCLIV2.msi
     ```
   - Instale o AWS CLI executando:
     ```shell
     Start-Process msiexec.exe -Wait -ArgumentList '/I AWSCLIV2.msi /quiet'
     ```
   - Verifique a instalação executando:
     ```shell
     aws --version
     ```

3. **Configuração das Credenciais da AWS:**
   - Configure suas credenciais da AWS executando o comando:
     ```shell
     aws configure
     ```
   - Forneça suas credenciais de acesso (AWS Access Key ID, AWS Secret Access Key, região padrão e formato de saída).

4. **Criação do Arquivo Terraform (main.tf):**
   - Crie um arquivo de configuração Terraform chamado `main.tf` com o conteúdo fornecido.

5. **Inicialização do Terraform:**
   - Abra o PowerShell no diretório onde está o arquivo `main.tf` e execute:
     ```shell
     terraform init
     ```

6. **Planejamento da Infraestrutura:**
   - Para ver o que será criado, execute:
     ```shell
     terraform plan
     ```

     ![image](https://github.com/sophiatosarr/build-infrastructure/assets/99216420/1cc4e059-929a-4fb5-a488-58eddd0c3c0d)
     ![image](https://github.com/sophiatosarr/build-infrastructure/assets/99216420/1ce69414-9f2c-46a7-ba5d-8c080ce05ab5)



7. **Aplicação da Configuração:**
   - Para criar a instância EC2, execute:
     ```shell
     terraform apply
     ```

     ![image](https://github.com/sophiatosarr/build-infrastructure/assets/99216420/d8fc5e6b-d9e9-4efc-bdac-6a85e4169222)

   - Digite yes quando solicitado para confirmar a aplicação da configuração.
  
     ![image](https://github.com/sophiatosarr/build-infrastructure/assets/99216420/06c8fb57-59e2-4514-8adb-d09a78026c20)


### Documentação dos Recursos Provisionados

**Recursos na Nuvem:**
- **Amazon EC2 Instance:**
  - Tipo: t2.micro
  - AMI: Amazon Linux 2 AMI (HVM), SSD Volume Type
  - Tags: Name=TerraformExample
