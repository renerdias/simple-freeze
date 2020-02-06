# simple-freeze

Olá pessoal, sou novo no fórum! gostaria de perguntar à vocês se existe alguma maneira de colocar senha no "Gofris", para que o administrador somente possa acesá-lo inserindo a senha. Tem como fazer isso? Obrigado!

---

https://unix.stackexchange.com/questions/59929/whats-the-difference-between-etc-rc-local-and-etc-init-d-rc-local

---

Not working in some distro's it needs to be updated /etc/rc.local does'nt exist in systemd 
---

Colocando script na inicialização do Linux (Ubuntu/Debian)


Essa dica é para quem não sabe como colocar um script na inicialização do sistema. Como se sabe, em distros como o Slackware basta você colocar seu script ou chamá-lo através do /etc/rc.d/rc.local.

Porém o Ubuntu e Debian não tem esse arquivo, então como fazer??? Muito simples. Basta você criar seu script dentro da pasta /etc/init.d. Exemplo:

# joe /etc/init.d/meuscript

#!/bin/bash

echo "Olá mundo"

Agora é só dar a permissão para execução:

# chmod 755 /etc/init.d/meuscript

Quase pronto, agora é só colocar para inicializar junto com o sistema:

# update-rc.d meuscript defaults


---
Complementando novamente! =)

Assim como o /etc/rc.d/rc.local é um shell script que é executado durante a inicialização do sistema, você também pode criar um que será executado durante a finalização do sistema. Veja:

Em '/etc/rc.d' crie um script com o seguinte nome: 'rc.local_shutdown', dê permissão de execução: 'chmod +x rc.local_shutdown' e pronto.

Exemplo:
------------
#!/bin/sh
#
# rc.local_shutdown - script que e executado
# durante a finalizacao (shutdown) do sistema.

# Removendo os arquivos temporarios criados em /tmp:
rm -rf /tmp/* 2> /dev/null
------------

Ao utilizar este exemplo, toda vez que o sistema for desligado ou reinicializado, os arquivos temporários em /tmp serão removidos.
---
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
