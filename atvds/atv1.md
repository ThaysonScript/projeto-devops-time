# 01. Estudo de Caso: O Incêndio Digital na MedTech Solutions

<hr>
<h2>Relato Individual</h2>
<h3>3. Disponibilidade (Availability)</h3>

- O que é: Garantir que os usuários autorizados tenham acesso à informação e aos ativos associados sempre que necessário.

- O Incidente: Irritados por não conseguirem roubar os dados, os criminosos iniciaram um ataque de Negação de Serviço Distribuída (DDoS), inundando os servidores da MedTech com milhões de acessos simultâneos para derrubar o sistema.

- A Defesa: A MedTech possuía uma infraestrutura de nuvem com balanceamento de carga (Load Balancers) e um serviço de mitigação de DDoS. O tráfego malicioso foi desviado, e servidores redundantes em outra região geográfica assumiram a carga de trabalho automaticamente.

- O Resultado: Os médicos nos hospitais continuaram acessando os prontuários em tempo real, sem interrupções no atendimento de emergência.

<p>

</p>

<hr>
<hr>
<h2>O Cenário</h2>

<p>
A MedTech Solutions gerencia o sistema HealthCloud, onde médicos inserem diagnósticos, prescrevem medicamentos e assinam laudos digitalmente. Os pacientes também têm acesso a um portal para baixar seus exames.
Recentemente, a empresa passou por um "dia de crise" que colocou à prova todos os cinco pilares da Segurança da Informação.
</p>

### 1. Confidencialidade (Confidentiality)
<p>
O que é: Garantir que a informação seja acessível apenas por pessoas autorizadas.
O Incidente: Um grupo de cibercriminosos tentou realizar um ataque de SQL Injection para extrair o banco de dados de pacientes famosos internados em um hospital parceiro.
A Defesa: Como a MedTech implementou criptografia de ponta a ponta nos dados em repouso (AES-256) e um sistema rígido de Controle de Acesso Baseado em Funções (RBAC), os atacantes até conseguiram acessar um fragmento do banco de dados, mas os dados estavam ilegíveis.
O Resultado: A privacidade dos pacientes foi mantida. A informação continuou sob sigilo, respeitando a confidencialidade.
</p>

### 2. Integridade (Integrity)
<p>
O que é: Garantir que a informação seja exata, completa e protegida contra modificações não autorizadas ou acidentais.
O Incidente: Durante a mesma semana, um erro de sincronização de rede corrompeu pacotes de dados no momento em que um médico alterava a dosagem de um medicamento de $5mg$ para $50mg$.
A Defesa: O sistema HealthCloud utiliza funções de hash (como SHA-256) para verificar a integridade de cada registro médico salvo. Quando o sistema detectou que o hash do arquivo recebido não batia com o hash do arquivo enviado, ele rejeitou a alteração e alertou o médico sobre o erro de comunicação.
O Resultado: A integridade evitou que um dado errôneo fosse gravado no prontuário, o que poderia ter causado a morte de um paciente.
</p>

### 3. Disponibilidade (Availability)
<p>
O que é: Garantir que os usuários autorizados tenham acesso à informação e aos ativos associados sempre que necessário.
O Incidente: Irritados por não conseguirem roubar os dados, os criminosos iniciaram um ataque de Negação de Serviço Distribuída (DDoS), inundando os servidores da MedTech com milhões de acessos simultâneos para derrubar o sistema.
A Defesa: A MedTech possuía uma infraestrutura de nuvem com balanceamento de carga (Load Balancers) e um serviço de mitigação de DDoS. O tráfego malicioso foi desviado, e servidores redundantes em outra região geográfica assumiram a carga de trabalho automaticamente.
O Resultado: Os médicos nos hospitais continuaram acessando os prontuários em tempo real, sem interrupções no atendimento de emergência.
</p>

### 4. Autenticidade (Authenticity)
<p>
O que é: Confirmar a identidade de um usuário ou da fonte de um dado; garantir que quem está enviando ou acessando é realmente quem diz ser.
O Incidente: Um hacker tentou se passar pelo Diretor Clínico do hospital usando técnicas de phishing para conseguir as credenciais de login e autorizar a liberação de medicamentos controlados.
A Defesa: O sistema exige Autenticação de Múltiplos Fatores (MFA) combinada com certificados digitais. Mesmo possuindo a senha correta, o atacante não conseguiu fornecer o segundo fator (biometria via aplicativo no celular do diretor).
O Resultado: O sistema barrou o acesso porque a identidade do usuário não pôde ser devidamente autenticada.
</p>

### 5. Não-repúdio (Non-repudiation)
<p>
O que é: Garantir que uma parte em uma transação/comunicação não possa negar a autoria de uma ação.
O Incidente: Um médico do hospital prescreveu por engano um remédio ao qual o paciente era alérgico. Após o susto (o paciente foi tratado a tempo), o médico alegou que "nunca havia feito aquela prescrição" e que o sistema deveria ter falhado ou sido invadido.
A Defesa: O HealthCloud utiliza assinaturas digitais com ICP-Brasil (padrão legal) e mantém logs de auditoria imutáveis (com timestamping ou carimbo do tempo). Ao auditar o sistema, a equipe de TI provou que a receita foi assinada com a chave privada exclusiva daquele médico às 14h32.
O Resultado: O médico não pôde negar a autoria da ação (não-repúdio), permitindo que o hospital fizesse o treinamento corretivo necessário e resolvesse a questão jurídica internamente.
</p>
