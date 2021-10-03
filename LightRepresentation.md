# Arduino-FabPro
const int LED_10 = 10;           // Порт 10, желтый светодиод
const int LED_9 = 9;             // Порт 9, красный светодиод
const int LED_8 = 8;             // Порт 8, желтый светодиод
const int LED_7 = 7;             // Порт 7, красный светодиод


const int TIMEOUT_10 = 300;          // Время горения красного сетодиода
const int TIMEOUT_9 = 169;          // Время горения желтого светодиода
const int TIMEOUT_8 = 300;          // Время горения красного сетодиода
const int TIMEOUT_7 = 169;          // Время горения желтого светодиода

void setup()
{
  // Все порты светодиодов будут у нас установлены в режим "внешняя нагрузка", OUTPUT
  pinMode(LED_10, OUTPUT);   
  pinMode(LED_9, OUTPUT);
  pinMode(LED_8, OUTPUT);   
  pinMode(LED_7, OUTPUT);
  
  // Устанавливаем начальное значение светодиодов
  digitalWrite(LED_10, LOW);
  digitalWrite(LED_9, LOW);
  digitalWrite(LED_8, LOW);
  digitalWrite(LED_7, LOW);
}  

void loop()
{
  // Включаем жёлтый цвет светофора
  digitalWrite(LED_10, HIGH);    // Включаем светодиод       
  delay(TIMEOUT_10);             // Ждем

  // Мигаем красным светодиодом 3 раза
  for (int i=0; i<3; i++)
    {
      digitalWrite(LED_9, LOW);         
      delay(TIMEOUT_9);                
      digitalWrite(LED_9, HIGH);        
      delay(TIMEOUT_9);                
    }  
  
  // Теперь отключаем красный и включаем желтый светодиод
  digitalWrite(LED_9, LOW); 
  digitalWrite(LED_10, HIGH);           
  delay(TIMEOUT_10);            

  // Отключаем желтый светодиод.
  digitalWrite(LED_10, LOW); 
  // Теперь включаем красный цвет
  digitalWrite(LED_7, HIGH);            
  delay(TIMEOUT_9);                         
          
  // Включаем желтый светодиод,не выключая красный
  digitalWrite(LED_8, HIGH);           
  delay(TIMEOUT_8);                       
  
  // Отключаем желтый и красный светодиоды.
  digitalWrite(LED_7, LOW);    
  digitalWrite(LED_8, LOW);   
  
}
