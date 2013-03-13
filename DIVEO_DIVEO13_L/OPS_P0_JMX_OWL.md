teste

**Command:** [http://service-registry.it.movile.com:29000/InvokeAction//MmcMonitor%3Atype%3DMmcMoExit/action=reCheckMoExitMonitoring?action=reCheckMoExitMonitoring](http://service-registry.it.movile.com:29000/InvokeAction//MmcMonitor%3Atype%3DMmcMoExit/action=reCheckMoExitMonitoring?action=reCheckMoExitMonitoring)   
**Server:** 200.189.169.13 e 200.189.169.28   
   
Procedimento N1:
----------------
+ Logar via ssh no servidor 200.219.220.99 e executar o comando: *remote-service 200.189.169.13 owl restart*
+ No nagios, clicar em "Re-schedule the next check of this service", clicar em Commit, clicar em Done, aguardar 10 minutos e verificar se o alarme sumiu. Caso não tenha sumido, acionar Nível 2.

Procedimento N2:
----------------
+ Verificar se o coruja esta UP
+ Caso não esteja inicia-lo: 
service owl start
+ Se o problema persistir, verificar se os servidores de banco de dados estão acessíveis:  
> *Base MMC: 200.189.1.169.20/mmc*  
> *Mirror Atlas MO: 200.18969.22/Atlas*  
> *Mirror SBS: owl.mirror-a.internal.db.it.movile.com/sbs*  
+ Caso todos os servidores de banco de dados estejam conectando corretamente, verifique se o usuário "coruja" possuí acesso ao servidor:  
> *200.189.169.20:1433/mmc*
+ Caso algum servidor seja restabelecido ou o acesso ao usuário coruja deja disponibilizado novamente, realize um restart do Owl (200.189.169.13  e 200.189.169.28)
+ Caso não haja sucesso entrar em contato com Andrew e equipe.  
PS.: Caso este alarme esteja em critical o script já irá enviar um email para sys@movile.com
