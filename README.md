# Voltímetro com Arduino

Este projeto implementa um voltímetro simples e um sistema PWM para variar a luminosidade de um led com base na resistencia de um potenciometro, 
utilizando o **Arduino Uno**. A leitura da tensão é feita através das entradas analógicas do microcontrolador e exibida em um monitor serial.  

![Pinagem ATmega328P](./arduino.jpg)

---

## 🧾 Descrição do Projeto

- O Arduino mede tensões aplicadas em suas portas **analógica (A0)**.    
- O valor lido (0–1023) é convertido em uma tensão real com base na referência de 5V (padrão) ou outra definida no código.  

--- 

## 🔌 Conexões

- **Entrada de tensão** → Pino **A0** (pode ser ajustado para A1–A5 via registradores).  
- **GND** do circuito de entrada → **GND** do Arduino.  
- Se a tensão a ser medida for maior que 5V, **use um divisor resistivo** para não danificar o microcontrolador.  

---

## ⚙️ Links dos projetos

[PWM_Basico](https://www.tinkercad.com/things/cQGWXXYht1i-pwdsimples/editel?returnTo=https%3A%2F%2Fwww.tinkercad.com%2Fdashboard&sharecode=2dRmmOqpC713eReGUSpG5k-hWhY2nGR9L7kIUWgsPC8)
[PWM_Registrador](https://www.tinkercad.com/things/e8BBa8WgEZe-registerpwdversion/editel?returnTo=%2Fdashboard%2Fdesigns%2Fcircuits&sharecode=-14tuVJkhdyf7kNK5CJ4Pf-45WHysT-jH8HmVM1h7ZM)

---

## 📐 Regra do Divisor de Tensão

Quando a tensão de entrada for maior que 5V, é obrigatório reduzir o valor com um **divisor resistivo**.  

A fórmula é:  

\[
V_{out} = V_{in} \times \frac{R2}{R1 + R2}
\]

- **Vin** → Tensão a ser medida.  
- **Vout** → Tensão que chega ao Arduino (máximo 5V).  
- **R1** e **R2** → Resistores do divisor.  

👉 Para calcular a tensão real:  

\[
V_{in} = V_{out} \times \frac{R1 + R2}{R2}
\]

### Exemplo prático:
Se você deseja medir até **20V**, pode usar:  
- `R1 = 15kΩ`  
- `R2 = 5kΩ`  

Assim:  

\[
V_{out} = 20V \times \frac{5k}{15k + 5k} = 5V
\]

Perfeito para o ADC do Arduino.  

---

