![Texto Alternativo](https://raw.githubusercontent.com/leonardoalvessousa/AVR_WDT/refs/heads/main/AVR_BANNER.jpg)

## Apresentação

Neste artigo será explorado o circuito  **`Device Watchdog Timer (WDT)`**, que esta presente nos dispositivos AVR® da Microchip Technology. O **`WDT`** é um mecanismo de segurança crucial que garante a estabilidade do sistema. Ele é útil para detectar falhas no software ou hardware, evitando que o sistema fique preso em um estado de erro.

### Diagrama simplificado

O `WDT` funciona como um contador, que realiza incrementos a cada ciclo de clock, de um oscilador independente do chip (O_WDT). Quando o contador atinge um valor predefinido, chamado de tempo limite, o `WDT` dispara e força a reinicialização do sistema.

![Texto Alternativo](https://raw.githubusercontent.com/leonardoalvessousa/AVR_WDT/refs/heads/main/BlocDiagram.jpg)

### Ativação do WDT

Realizando um exemplo prático usando o Chip ATmega328p na IDE Arduino

```IDE_Arduino
// C++

#include <avr/wdt.h>

void setup() 
{
  wdt_enable(WDTO_2S);
}
void loop() 
{
  // Tarefa principal
}
```

> Inclusão da biblioteca WDT

- **#include:** Essa diretiva indica ao compilador que ele deve incluir o arquivo de cabeçalho `avr/wdt.h`.
- **avr/wdt.h:** Esse arquivo de cabeçalho contém as definições e funções necessárias para trabalhar com o WDT em dispositivos AVR.

> Tarefa inicial

- **void setup():** Essa função é chamada uma vez no início do programa. É onde você configura as configurações iniciais do seu programa.
-  **wdt_enable():** Essa função é definida no arquivo `avr/wdt.h` e habilita o WDT.
- **WDTO_2S:** Essa constante, também definida no arquivo `avr/wdt.h`, configura o tempo limite do WDT para 2 segundos.

 > [!NOTE]
> Existem outros TIMEs pré definidos pela bibliote `avr/wdt.h`, segue a lista:
>
> `wdt_enable(WDTO_8S);`
> `wdt_enable(WDTO_4S);`
> `wdt_enable(WDTO_1S);`
>  `wdt_enable(WDTO_500MS);`
>  `wdt_enable(WDTO_250MS);`
>  `wdt_enable(WDTO_1200MS);`
>  `wdt_enable(WDTO_60MS);`
>  `wdt_enable(WDTO_30MS);`
>  `wdt_enable(WDTO_15MS);`
>  > Segundo (S), Milissegundo (MS)

> Tarefa principal/loop

- **void loop():** Essa função é chamada repetidamente após a função `setup()` ser executada.

### Considerações finais

Sempre verifique os atrasos comuns existentes na tarefa principal como: Delay; Subfunções com múltiplas tarefas complexas. Estes atrasos devem ser levados em consideração na escolha do timer da função `wdt_enable()`.

> [!CAUTION]
> Evitando resets desnecessários gerados pelos processos normais do algoritmo. Realize alguns cálculos!!!

## 😼 Autor

 🐈‍⬛ @leonardoalvessousa

## 🎁 Expressões de gratidão

* Conte a outras pessoas sobre este projeto 📢;
* Convide o autor para uma cerveja 🍺;
* Um agradecimento publicamente ou citação 🫂;
* etc.
