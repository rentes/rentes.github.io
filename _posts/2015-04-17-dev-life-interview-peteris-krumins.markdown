---
layout: post
title:  "dev.life - interview with Peteris Krumins"
date:   2015-04-17 10:49:23
comments: true
---

The following interview is a personal translation to the Portuguese language of the interview with Peteris Krumins for the dev.life series on the [Fog Creek blog][fogcreek-blog]. You can access the original interview [here][fogcreel-interview-peteris-krumins].

# dev.life - Entrevista com Peteris Krumins

Na série de entrevistas dev.life, conversamos com programadores sobre a sua paixão por programação: como começaram, em que tópicos gostam de trabalhar e como o fazem.

O convidado de hoje é [Peteris Krumins][peteris-krumins-twitter], co-fundador e CEO da [Browserling][browserling], um serviço online de testes em diferentes navegadores web. Ele também é o autor de '[Perl One-Liners][perl-one-liners]', um livro sobre resolver rapidamente problemas na linha de comandos usando a linguagem Perl. Escreve regularmente sobre desenvolvimento de software no seu [blog][peteris-krumins-blog].


***

![Peteris Krumins](http://blog.fogcreek.com/wp-content/uploads/2015/04/peter.png "Peteris Krumins")

**Localização**: São Franciso, EUA

**Posição actual**: CEO da Browserling

***

## Como começaste a desenvolver software?

Eu tenho usado computadores já desde os meus 6 anos quando comecei a ter acesso a um computador 386 ou 486 no trabalho da minha mãe. A primeira vez que me sentei em frente de um computador fiquei completamente viciado. A partir daí, todos os dias ficava a sonhar em ter o meu próprio computador. Demorei algum tempo até conseguir ter um computador, e até o conseguir, tentei ter acesso a um em qualquer lugar em que fosse possível. No processo, fiz uma tonelada de amigos que estavam interessados em computadores e que usavam os seus próprios computadores. Até cheguei a fingir ser um estudante em diversas universidades, enquanto era apenas uma criança, só para ter acesso à Internet!

Na realidade, comecei por ter um portátil em primeiro lugar. Tinha um amigo chamado Zombie e ele era um administrador de sistemas incrível. De alguma forma, ele tinha um portátil de substituição e deu-mo gratuitamente. Eu ainda o tenho. Era um portátil IBM Butterfly (ThinkPad 701CS). Tinha 8 MB de RAM, disco de 800MB, e um *dual boot* com Windows 95 e OpenBSD. Mais tarde, fiz uma actualização para 40MB de RAM. Tinha também uma placa de rede PCMCIA *thinnet* e a minha primeira rede doméstica era de 10 Mbit/s em thinnet. Para quem nunca ouvir falar de thinnet, é Ethernet sobre cabo coaxial, também conhecida por 10BASE2.

![Portatil antigo](http://blog.fogcreek.com/wp-content/uploads/2015/04/old_comp-1.png "O primeiro portátil")

Finalmente consegui ter o meu próprio computador muito mais tarde quando tinha 15 anos de idade. Era uma máquina fantástica com um processador Celeron de 400MHz, com 256MB de RAM, um disco de 8GB, uma placa gráfica 3D Blaster Banshee de 16MB, e um monitor CRT de 17" a 75Hz com uma resolução de 1024x768. Este computador corria o Windows 98 que tinha acabado de sair.

Eu sou 100% autodidata. Comecei a aprender um conjunto de linguagens de programação diferentes ao mesmo tempo. Pela altura em que consegui ter o meu computador Celeron, já tinha um entendimento claro do que eu queria fazer no futuro. Eu queria fazer páginas web, e assim logo no primeiro dia em que tive o meu computador, comecei a escrever em HTML, JavaScript e CSS. A princípio, não entendia muito bem como é que os sites funcionavam e não sabia sobre as linguagens do lado do servidor, o que me levou algum tempo até entender que iria precisar de um servidor web para executar os meus sites. Estava a hospedar os meus sites na Angelfire no início, mas mais tarde montei o meu próprio servidor web Linux Slackware com PHP e MySQL. Também queria ser um hacker e daí ter aprendido C e Assembly. Passei quantidades ridículas de tempo na IRCNet, e daí que tenha aprendido scripting mIRC, bem como ter criado o meu próprio cliente de IRC em Visual Basic.

## Fale-nos um pouco sobre a tua posição actual

O meu trabalho actual é ser CEO da Browserling. Criei a Browserling em 2011 na Área da Baía de São Francisco juntamente com um amigo. O meu típico dia de trabalho resume-se a escrever muito código, gerir servidores, trabalhar com os clientes e os meus empregados. Adoro o que faço e actualmente não me imaginava a fazer outro trabalho que não seja o de gerir uma empresa de software. Sou um fã enorme do Paul Graham e os seus ensaios encorajaram-me a começar a minha startup.

Actualmente estou 100% focado no crescimento do meu negócio. Não faço projectos paralelos e parei de escrever livros uma vez que isso que mudaria a minha atenção da empresa. A regra número um de construir uma empresa de sucesso é ter 100% de foco no produto. Actualmente estou a aumentar as receitas e a construir uma equipa remota internacional na Browserling. Acabei de contratar um engenheiro fantástico na Ucrânia e estou a expandir a empresa para mercados que não tenham o Inglês como língua materna.

Estou também ocupado a resolver uma série de problemas técnicos, tais como conseguir transmitir eficientemente navegadores a correr em máquinas virtuais para clientes, e como capturar centenas de *screenshots* do navegador por segundo. Adoro trabalhar com servidores e estou a planear mudar a *stack* do servidor de instâncias na *cloud* em EC2 e Rackspace para hardware real. Os servidores na cloud são interessantes quando se começa um negócio, mas uma vez que consigas atingir um determinado ponto, faz mais sentido mudar para o teu próprio hardware. Assim consegue-se poupar muito dinheiro e aumenta também o desempenho.

## Quando é que estás mais feliz a programar?

Estou mais feliz quando estou [na zona][get-into-the-zone] e quando eu consigo fazer as coisas (*Getting Things Done*). Sou capaz de entrar na zona muitas vezes e posso compartilhar o meu segredo. Estou acordado durante a noite e durmo o durante o dia. Para mim trabalhar de noite é a altura perfeita para estar na zona. A noite elimina todas as distracções e mantém-te alerta e focado. Outro segredo para estar na zona é fechar o Twitter, Facebook, Skype, Gtalk, G+. Quando estás na zona não queres ser incomodado subitamente por alertas sonoros ou mensagens.

![Novo computador](http://blog.fogcreek.com/wp-content/uploads/2015/04/new_comp-1.png "O novo computador")

## Qual é o teu ambiente de desenvolvimento?

Eu tenho uma configuração Windows/Linux. Uso Windows 7 na minha estação de trabalho principal e ligo-me por SSH aos meus servidores Linux. Acabei de construir uma nova estação de trabalho no mês passado. Adquiri um processador Intel i7 4790K e fiz *overclock* para 4.7GHz.

Tenho um servidor *firewall* Linux, um servidor de ficheiros Linux e um servidor de desenvolvimento Linux. Monto o servidor de ficheiros Linux no Windows através do Samba, que corre uma série de discos em RAID 6, o que me permite continuar a trabalhar mesmo que hajam falhas em dois discos em simultâneo. Todos estes servidores Linux correm Slackware. Adoro a simplicidade do Slackware. Eu prefiro as instalações minimalistas e, em seguida, adiciono apenas os pacotes de que preciso. Assim, por exemplo, o servidor de firewall não tem muito mais do que Bash, Vim e Iptables. O servidor de ficheiros tem Bash, Vim, Cryptsetup e Samba. E o servidor de desenvolvimento tem tudo o que eu preciso para o desenvolvimento.

Uso Vim em Windows e Linux, e gVim e Visual Studio em Windows. Não consigo imaginar programar aplicações Windows num ambiente sem IntelliSense. Tenho um [Vim altamente customizado][vim] no qual uso umas duas dúzias de [plugins][vim-plugins], tais como:

- surround.vim (rapidamente editar texto)
- repeat.vim (repetir comandos)
- matchit.vim (extender o que a chave % encontra)
- snipmate.vim (*snippets* de código)
- nerd_tree.vim (explora o sistem de ficheiros a partir do vim)
- a.vim (alternar entre ficheiros C e *headers*)
- ragtag.vim (mapeamentos para editar HTML)
- tabular.vim (alinhar texto)
- bufexplorer.vim (trabalhar com buffers)
- python.vim (melhor suporte para python)
- exchange.vim (alternar texto rapidamente)
- abolish.vim (substituir palavras)
- speeddating.vim (incrementar datas)

entre outros.

Em Windows, não conseguiria viver sem:

- Total Commander (gestor de ficheiros)
- Visual Studio (não há melhor que o IntelliSense)
- SQLyog (gestor GUI para bases de dados MySQL)
- SQLiteSpy (gestor GUI para bases de dados SQLite)
- pgAdmin (gestor GUI para bases de dados PostgreSQL)
- WinSCP e SecureFX (clientes seguros de FTP)
- Putty e SecureCRT (clientes SSH)
- KeePass (gestor de palavras-passe)
- ClipX (gestor de *clipboard*)
- Launchy (lançador de programas)
- Locate32 (indexador de ficheiros)
- allSnap (gestor de janelas)
- AutoHotkeys (automatizar tarefas e programas)
- Virtual CloneDrive (montar imagens de disco)
- IsoBuster (extrair imagens de disco)
- ImgBurn (gravador de imagens)
- Enounce MySpeed (acelera ou atrasa vídeos)
- Hex Workshop (editor hexadecimal)
- VMWare Workstation (máquinas virtuais)
- Cygwin (ferramentas unix)
- UltraMon (suporte para múltiplos ecrãs)
- Beyond Compare (ferramenta de diferenças)
- Tclock2 (um melhor relógio)
- Fineprint (proxy de impressoras)
- SumatraPDF (um melhor visualizador de ficheiros PDF)
- AviSynth (editar vídeos programaticamente)
- ffmpeg (conversor vídeo)
- VirtualDub (converte e edita vídeos)
- WinDirStat (visualização do espaço em disco)
- clink (um melhor cmd.exe)
- IDA Pro (*debugging*)
- Photoshop
- Sysinternals tools

Em Linux, não conseguiria viver sem:

- samba (montar Linux em Windows)
- tmux and screen (sessões shell persistentes)
- todas as ferramentas standard UNIX (awk, sed, grep, head, tail, uniq, sort, etc.)
- perl (prototipagem rápida, hacks rápidos, *one-liners*)
- iptables e nftables (firewalling)
- htop (um melhor top)
- mtr (um melhor traceroute)
- multitail (tail a múltiplos ficheiros em múltiplas janelas)
- nc (netcat, canivete suíço TCP/IP)
- iftop (monitor de largura de banda)
- ack (um melhor grep)
- ipcalc (calculadora de endereços de rede)
- pv (pipe viewer – barra de progresso de *pipes* UNIX)
- rsync (*backups*)
- ncdu (visualização do espaço em disco)
- curl (cliente HTTP)
- nmap (*scanner* de rede)
- tcpdump e wireshark (*debugging* de rede)
- sysdig (strace + lsof + tcpdump combinados)
- youtube-dl (descarregar todos os vídeos online)

entre outras ferramentas.

Eu programo sentado. Eu nunca tentei programar em pé ou a andar. Isso parece-me muito estranho. Quando eu estou na zona, eu escuto a transmissão *Vocal Trance* a partir de [di.fm][di-fm]. Mas só se eu estou na zona. Caso contrário, a música é um foco de distracção. Eu não poderia ter programado sem um teclado Microsoft Natural. Tive o meu por mais de 10 anos. Ainda funciona bem, mas está a mostrar sinais de degradação.

Eu tomo um monte de notas ao tentar descobrir como alguma coisa funciona. Quando tenho um problema mais complicado para resolver, tento primeiro dividi-lo em sub-tarefas menores, que podem ser facilmente resolvidas. Em seguida, crio uma lista de tarefas, faço-as uma por uma, e risco da lista de tarefas. Na realidade, tenho várias listas de tarefas de longo prazo (para os próximos 1-2 anos), de médio prazo (para os próximos meses) e tarefas de curto prazo que estou a fazer agora.

## Quais são os teus livros/recursos preferidos sobre desenvolvimento de software?

Sou doido por livros sobre computadores e livros de Ciência em geral. Regularmente, de tempos a tempos, perco um dia a pesquisar a última literatura e a comprar os títulos mais interessantes para mim. Vou listar o meu top 5 de livros de codificação, programação e computadores.

- [The New Turing Omnibus][turing-omnibus]
A não perder para qualquer pessoa interessada por computadores. Este excelente livro contém 66 ensaios curtos sobre os mais importantes e interessantes tópicos de computação, tais como, máquinas de Turing, gramáticas formais, funções não-computáveis, e redes neuronais. O estilo de escrita deste livro é casual e não contém praticamente nenhuma matemática. É o meu livro favorito de todos os tempos.

- [The Little Book of Semaphores][book-semaphores]
Este livro ensina como pensar sobre execução em múltiplas *threads* e como resolver problemas de sincronização. Recomendo-o enormemente, especialmente se és alguém que aprende por ti mesmo. Este livro leva o leitor passo-a-passo a uma série de problemas clássicos e outros não tão clássicos de sincronização. É bastante divertido trabalhar nestes problemas e tenho-o recomendado a todas as pessoas desde que encontrei este livro.

- [Programming Pearls][programming-pearls] e [More Programming Pearls][more-programming-pearls]
Livros clássicos de programação. O Jon Bentley sabe como escrever de forma clara e entusiástica sobre algoritmos. Estes livros são intemporais e ensinam-te a como raciocinar sobre os problemas, a dividi-los em problemas mais pequenos, e a implementar soluções eficientemente. Vais certamente passar à entrevista na Google se leres estes dois livros.

- [The Little Schemer][little-schemer]
O *Little Schemer* ensina-te um pouco de LISP no estilo mais divertido de sempre. O livro é um diálogo entre ti e os autores sobre centenas de pequenos programas em Scheme e ensina-te a pensar recursivamente. Este livro vai fazer-te pensar e vai estimular a tua mente um pouco. É um dos livros de programação mais divertidos alguma vez escritos.

- [The Elements of Style][elements-style] e [The Elements of Programming Style][elements-programming-style]
O *The Elements of Style* não é exactamente um livro de desenvolvimento de software ou de codificação, mas antes um livro sobre como escrever. Para se ser um grande programador tens de saber comunicar de forma clara e ter proficiência na escrita é essencial. São só 100 páginas e lê-se numa tarde.
O *The Elements of Programming Style* é um livro de programação clássico pelo Kernighan e a forma deste livro é altamente influenciada pelo *The Elements of Style*. É um livro antigo mas praticamente tudo o que ensina ainda se aplica aos dias de hoje. Contém 70 regras de programação, como por exemplo, Escreve de forma clara: não sejas esperto demais. Escreve o que queres dizer de forma simples e directa. Escolhe uma representação dos dados que torne o teu programa simples. Deixa os dados estruturarem o programa.

E eu ainda agora comecei. Podia facilmente fazer o meu top 100 de livros preferidos. Envia-me uma mensagem se precisares de algum conselho de livro para ler ou se quiseres falar de livros comigo!

![Estante de livros](http://blog.fogcreek.com/wp-content/uploads/2015/04/bookshelf-1.png "Estante de livros do Peteris")

## Que tecnologias estás actualmente a experimentar?

Sou um enorme fã do Visual Studio e acabei de descarregar o Visual Studio 2015 Preview, e tenho andado a experimentá-lo. Também instalei o Windows 10 Preview numa máquina virtual. Uma vez que eu faço testes em diferentes navegadores web, estou realmente na expectativa de saber como será o próximo navegador web da Microsoft chamado Spartan e o que este vai oferecer.

A Google acabou de disponibilizar em código aberto o [Kythe][kythe], que deverá ser um indexador e pesquisador de código muito melhor do que o que existe actualmente. Soube deste projecto através de um amigo que trabalha na Google e desde então que tenho estado impacientemente à espera deste projecto. Vou experimentá-lo no código do kernel Linux este fim-de-semana.

Se eu tivesse mais tempo, combinaria o Oculus Rift com uma plataforma de deslocação para construir um verdadeiro equipamento de realidade virtual.

## Quando não estás a programar, o que gostas de fazer?

Eu gosto de me manter em forma. Eu pratico atletismo. Descobri que correr pistas é bem melhor do que tomar café. Nos dias em que eu faço *sprints* de 10x60m fico com energia para 10-12 horas e consigo programar a noite toda. Também gosto de competir em competições de atletismo. As corridas de 400m e 800m são as minhas distâncias favoritas.

## Que conselho darias ao teu eu mais novo que estivesse agora a começar a programar?

Consigo pensar em quatro conselhos a dar ao meu eu mais novo:

- Resolve os problemas rapidamente e eficazmente, e segue em frente.
- Não desenvolvas software que não traga valor.
- Começa um blog de software o quanto antes.
- Disponibiliza o código cedo e muitas vezes.


[book-semaphores]: http://greenteapress.com/semaphores
[browserling]: https://www.browserling.com/
[di-fm]: http://www.di.fm/
[elements-programming-style]: http://www.amazon.com/The-Elements-Programming-Style-Edition/dp/0070342075
[elements-style]: http://www.amazon.com/Elements-Style-Fourth-William-Strunk/dp/020530902X
[fogcreek-blog]: http://blog.fogcreek.com/
[fogcreek]:      http://www.fogcreek.com/
[fogcreel-interview-peteris-krumins]: http://blog.fogcreek.com/dev-life-interview-with-peteris-krumins/
[get-into-the-zone]: http://www.techurbia.com/2009/02/how-to-get-into-the-zone-as-a-programmer.html
[kythe]: http://www.kythe.io/
[little-schemer]: http://www.amazon.com/The-Little-Schemer-4th-Edition/dp/0262560992
[more-programming-pearls]: http://www.amazon.com/More-Programming-Pearls-Confessions-Coder/dp/0201118890
[perl-one-liners]: http://www.nostarch.com/perloneliners
[peteris-krumins-blog]: http://www.catonmat.net/
[peteris-krumins-twitter]: https://twitter.com/pkrumins
[programming-pearls]: http://www.amazon.com/Programming-Pearls-2nd-Jon-Bentley/dp/0201657880
[turing-omnibus]: http://www.amazon.com/The-New-Turing-Omnibus-Excursions/dp/0805071660
[vim-plugins]: http://www.vim.org/scripts/
[vim]: http://www.catonmat.net/series/vim-plugins-you-should-know-about
