================================================================================
= = = = = = = = = = = = =   Leia-me do Thunderbird  = = = = = = = = = = = = = = =
================================================================================

O Thunderbird est� sujeito aos termos em detalhe na licen�a que o acompanha.

Este ficheiro Read Me cont�m informa��es sobre os requisitos de sistema e
instru��es de instala��o e compila��o do Thunderbird para OS/2.

Para mais informa��es sobre o Thunderbird, visite
	http://www.mozilla.org/products/thunderbird/.

Para mais informa��o sobre a porta OS/2 visite http://www.mozilla.org/ports/os2.

Para submeter erros ou sugest�es visite o Bugzilla em
	https://bugzilla.mozilla.org
para links para erros conhecidos, guias para a notifica��o de novos erros, e
muito mais. Pode tamb�m obter ajuda com o Bugzilla utilizando o seu cliente de
IRC para ir ao canal #mozillazine no servidor irc.mozilla.org. Problemas
espec�ficos do OS/2 s�o discutidos no canal #warpzilla e na lista de discuss�o
netscape.public.mozilla.os2 no news.mozilla.org e em outros servidores de


================================================================================
                          Como Obter o Thunderbird
================================================================================

As compila��es Milestone oficiais do Thunderbird est�o publicadas na p�gina de
lan�amentos em

  http://www.mozilla.org/products/thunderbird/releases/

Os lan�amentos para OS/2 n�o s�o criados pela equipa do Mozilla.org e podem
aparecer na p�gina http://www.mozilla.org/ports/os2 antes de aprarecerem na
p�gina dos lan�amentos. Tenha a certeza que de l� todas as notas de lan�amento
do Thunderbird ligadas � p�gina de lan�amentos para informa��es sobre os erros
conhecidos e quest�es de instala��o Thunderbird.


================================================================================
                        Requerimentos do sistema para OS/2
================================================================================

- Este lan�amento requer DLLs de execu��o C actualizadas (libc-0.5.1) do
	http://www.innotek.de/products/gccos2/download/gccos2download_e.html
para que possa ser executado. Por pre-defini��o as rotinas de instala��o s�o 
instaladas em \OS2\DLL na sua drive de arranque (bootdrive), mas pode coloc�-las 
na mesma directoria do execut�vel do Thunderbird, ou no LIBPATH do seu sistema.

- Requisitos m�nimos de hardware
  + Processador Pentium class
  + 64 MiB RAM mais 64 MiB de espa�o swap livre
  + 35 MiB de espa�o em disco livres para a instala��o mais espa�o de
  armazenamento para a cache do disco

- Hardware recomendado para um desempenho aceit�vel
  + 500 MHz de processador
  + 256 MiB RAM mais 64 MiB de espa�o swap livre
    NOTA: O desempenho e a estabilidade do Thunderbird aumenta quanto mais
    mem�ria RAM estiver dispon�vel. Especialmente para sess�es longas
    512 MiB de mem�ria � recomendado.
  + Placa gr�fica e driver capaz de mostrar mais de 256 cores

- Requisitos de software
  + Instala��o num sistema de ficheiros que suporte nomes de ficheiros longos
    (ex. HPFS ou JFS mas n�o FAT)
  + OS/2 Warp 4 com Fixpack 15 ou posterior
  + MPTS vers�o 5.3
  + TCP/IP vers�o 4.1
  + INETVER: SOCKETS.SYS=5.3007, AFOS2.SYS=5.3001, AFINET.SYS=5.3006
    NOTA: N�o tente utilizar MPTS & TCP/IP com vers�es abaixo dos n�veis
    INETVER. Apesar de o Thunderbird aparentemente iniciar e correr normalmente
    com estes stacks mais antigos, algumas funcionalidades que o Thunderbird
    necessita ainda n�o est�o implementadas correctamente em vers�es MPTS
    mais antigas, o que pode resultar em erros e perda de dados.

  + Convenience Pack 2 ou eComStation 1.0.


================================================================================
                          Instru��es de Instala��o
================================================================================

For all platforms, unpack into a clean (new) directory.  Installing on top of
previously released builds may cause problems with Thunderbird.

Note: These instructions do not tell you how to build Thunderbird.
For info on building the Thunderbird source, see

  http://www.mozilla.org/build/


OS/2 Installation Instructions
------------------------------

   On OS/2, Thunderbird does not have an installation program. To install it,
   download the .zip file and follow these steps:

     1. Click the "Zip" link on the site you're downloading Thunderbird from
     to download the ZIP package to your machine. This file is typically called
     thunderbird-*-os2.zip where the "*" is replaced by the Thunderbird version.

     2. Navigate to where you downloaded the file and unpack it using your
     favorite unzip tool.

     3. Keep in mind that the unzip process creates a directory "thunderbird"
     below the location you point it to, i.e. 
        unzip thunderbird-1.0-os2.zip -d c:\thunderbird-1.0
     will unpack Thunderbird into c:\thunderbird-1.0\thunderbird.

     4. Make sure that you are _not_ unpacking over an old installation. This is
     known to cause problems.

     5. To start Thunderbird, navigate to the directory you extracted
     Thunderbird to, make sure that the C library DLLs are copied to the
     installation directory or installed in the LIBPATH, and then double-click
     the Thunderbird.exe object.


Executar m�ltiplas vers�es em simult�neo
--------------------------------------

Devido aos v�rios membros da fam�lia Mozilla (ex. Mozilla, Thunderbird,
Thunderbird, IBM Web Browser) poderem utilizar vers�es diferentes ou
incompat�veis das mesmas DLLs, alguns passos extra s�o necess�rios para
os executar em simult�neo.

Uma forma de contornar o problema � utilizando a vari�vel LIBPATHSTRICT.
Para executar o Thunderbird um pode criar um script CMD como no exemplo
seguinte (onde � assumida uma instala��o do Thunderbird no direct�rio
d:\internet\Thunderbird):

	set LIBPATHSTRICT=T
	rem A linha seguinte pode ser necess�ria quando um programa diferente do  Mozilla program est� listada no LIBPATH
	rem set BEGINLIBPATH=d:\internet\Thunderbird
	rem A linha seguinte s� � necess�ria para executar duas vers�es diferentes do  Thunderbird
	rem set MOZ_NO_REMOTE=1
	d:
	cd d:\internet\thunderbird
	thunderbird.exe %1 %2 %3 %4 %5 %6 %7 %8 %9

Da forma semelhante, podemos criar um objecto de programa para iniciar o
Thunderbird utilizando as seguintes defini��es:

   Caminho e nome do ficheiro:	*
   Par�metros:					/c set LIBPATHSTRICT=T & .\thunderbird.exe "%*"
   Direct�rio de trabalho:		d:\internet\thunderbird

(Pode ainda necessitar de adiconar MOZ_NO_REMOTE e/ou BEGINLIBPATH como
no script CMD em cima dependendo da configura��o do sistema.)

Finalmente, o m�todo mais simples � utilizando o utilit�rio Run! por
Rich Walsh que pode ser encontrada no arquivo de software da Hobbes:

	http://hobbes.nmsu.edu/cgi-bin/h-search?key=Run!

Leia a documenta��o do utilit�rio para mais informa��es.


Separando perfis do direct�rio de instala��o
-----------------------------------------------

Para separar as localiza��es do perfil de utilizador(es) (contendo os
marcadores e todas as personaliza��es) do direct�rio de instala��o
para manter as suas prefer�ncias no caso de actualiza��o at� mesmo
quando utilizando pacotes ZIP, defina a vari�vel MOZILLA_HOME para
um direct�rio � sua escolha. Pode fazer isto ou no Config.sys ou num
script ou utilizando um objecto de programa como o listado acima.
Se adicionou

   set MOZILLA_HOME=f:\Data

o perfil de utilizador ser� criado em "f:\Data\Mozilla\thunderbird".

Se estiver a migrar do Mozilla, a rotina de importa��o do Thunderbird s�
ir� encontrar os dados do perfil existente se MOZILLA_HOME estiver
correctamente definida e a apontar para o Mozilla.


Outras vari�veis de ambiente importantes
-------------------------------------

Existem algumas vari�veis de ambiente que podem ser utilizadas para
controlar um comportamento especial do Thunderbird no OS/2:

- set NSPR_OS2_NO_HIRES_TIMER=1
  Isto far� com que o Thunderbird n�o utilize o temporizador de alta
  resolu��o do OS/2. Defina-a se outras aplica��es que utilizem este
  temporizador (aplica��es multim�dia) estejam a agir de modo estranho.

- set MOZILLA_USE_EXTENDED_FT2LIB=T
  Se tiver o Innotek Font Engine instalado, esta vari�vel activa
  fun��es especiais no Thunderbird para operar com caracteres unicode.

- set MOZ_NO_REMOTE=1
  Utilize isto para executar duas inst�ncias do Thunderbird em simult�neo
  (como por exemplo uma vers�o em depura��o e outra optimizada).

Encontre mais informa��o sobre este t�pico e outras dicas em
   http://www.os2bbs.com/os2news/Warpzilla.html


Problemas conhecidos da vers�o para OS/2
----------------------------------

Problemas multi-plataforma s�o geralmente listados nas notas de
lan�amento de cada lan�amento milestone.

- Bug 167884, "100% CPU load when viewing site [tiling transparent PNG]":
  https://bugzilla.mozilla.org/show_bug.cgi?id=167884
No OS/2, o motor de renderiza��o do Mozilla � conhecido por ter um
desempenho extremamente lento em sites que utilizem imagens pequenas e
repetidas com transpar�ncia no seu layout. Isto afecta tamb�m a
renderiza��o no Thunderbird.

Outros problemas conhecido podem ser encontrados seguindo o seguinte
link "Current Open Warpzilla Bugs" na p�gina do OS/2 no
Mozilla <http://www.mozilla.org/ports/os2/>.