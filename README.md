# TERCEIRA--PROVA

#define LED 4
#define BUTTON01 7
#define BUTTON02 2
int cont = 0;

#define setBit(valor,bit)(valor |= (1<<bit)) //OU
#define clearBit(valor,bit)(valor &= ~(1<<bit))//AND
#define toggleBit(valor,bit)(valor^=(1<<LED))//OU EXCLUSIVO
#define testeBit(valor, bit)(valor &(1<<bit))//NOT

void setup()
{
  pinMode(BUTTON01,INPUT_PULLUP); //SEM RESISTOR
  pinMode(BUTTON02,INPUT_PULLUP);
  setBit(DDRB, LED); // Para LED = 4, B3(D12) como saída
  clearBit(DDRB,BUTTON01);
  clearBit(DDRB,BUTTON02);// configura o pino D@ como entrada
}

void loop()
{

  if(!testeBit(PIND, BUTTON01) && (cont < 3))
  {
    setBit(PORTB, LED);
    delay(500);
    cont++;
    if(cont == 3)
    {
      clearBit(PORTB, LED);
      cont = 0 ;
    }
  }
   
}
