# Decisoes da pratica A

Explique, com referencia a uma chamada do programa:

1. Na falta de calibracao, qual funcao lanca, qual apenas propaga e qual recupera a falha? Responda para C++ e Python.

Em C++, a funcao adquirir verifica se a fonte esta calibrada. Se nao estiver, ela lanca a FalhaCalibracao. A funcao lerServico apenas chama a adquirir, entao ela deixa o erro passar. Depois, a executarCiclo pega essa falha e informa que o motivo foi calibracao.

Em Python acontece a mesma coisa. A adquirir lanca a FalhaCalibracao, a ler_servico apenas passa o erro para frente e a executar_ciclo captura a falha e informa calibracao.




2. Por que a captura de `FalhaCalibracao` vem antes da de `FalhaLeitura`? Quando a sessao e liberada em cada linguagem?

A FalhaCalibracao vem primeiro porque ela e mais especifica e herda da FalhaLeitura. Se a FalhaLeitura viesse primeiro, ela pegaria tambem a falha de calibracao e nao seria possivel identificar o motivo certo.

A sessao e liberada mesmo quando acontece um erro. No C++, isso acontece quando o objeto Sessao e destruido. No Python, o finally garante que a sessao seja fechada.




3. Como `FonteNivel` e `FonteConstante` podem ser consultadas pelo mesmo contrato? Dê um exemplo observado em `make run`.

As duas fontes seguem o mesmo contrato IFonteLeitura, porque as duas possuem valor() e unidade(). Assim, o programa consegue usar as duas da mesma forma.

No make run, a FonteConstante retorna 42.5 % e a FonteNivel retorna a leitura do sensor, que aparece como 20.
