# simple-freeze

Outro sistemas - antes de instalar faça backup dos usuários com o script:

#!/bin/bash
##   Programa para fazer backup de diretórios dos usuários
validos=$(grep "10..:" /etc/passwd) # usa-se o 10..: por causa dos inodes dos usuários
for users in $validos
do
   login=$(echo "$users" | cut -d : -f 1)
   homedir=$(echo "$users" | cut -d : -f 6)
   tar -cjf /srv/bkp_$login.tar.bz2 $homedir
done

O que está é "Deep Freeze"? Deep Freeze, por Faronic, é um aplicativo para Microsoft Windows e Mac OS X, que restaura o computador de volta à sua configuração original cada vez que o sistema for reiniciado.

Em Kubuntu o mesmo pode ser feito usando Ofris. Ofris é uma ferramenta de linha de comando, fácil de usar e oferece opções para bloquear o sistema para um usuário específico ou para todos os usuários. Ofris apenas congela o diretório home dos usuários, aplicativos instalados, enquanto o sistema está bloqueado permanecerá instalado após desbloqueio.

Há também um App Indicador disponível, que atende pelo nome de Gofris, o que torna todas as opções disponíveis Ofris com um par de cliques.

Não há pacote disponível no PPA, As instruções devem trabalhar para máquinas de 32 e 64 bits.

Ofris e Gofris são pacotes conflitantes. Escolha um para instalar, não é possível instalar ambos.
