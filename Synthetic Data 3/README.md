# Explicação dos Dados

Este conjunto de dados contém dados gerados sinteticamente pelo 3° modelo criado. O grafo gerado é uma malha quadrada de tamanho 10x10 considerando apenas os vértices internos. Cada vértice da borda está conectado a um vértice que atua como vértice de entrada e saída. Além disso, cada vértice do grafo representa uma via de 1km e com limite de velocidade de 50km/h. Cada amostra da série foi gerada com intervalo de 5 minutos, e o total de amostras corresponde a 2 meses de dados. Cada vértice de entrada possuia as seguintes funções de geração dos veículos:

```python
def daily_periodicy(self, clock):
        hour = clock.hour
        if 1 <= hour <= 4:
            return [exp_generator(1, 1)]
        elif hour == 23 or hour == 0 or hour == 5:
            return [exp_generator(0.75, 1)]
        elif hour == 6 or 21 <= hour <= 22:
            return [exp_generator(0.75, 1), exp_generator(1, 1)]
        elif 7 <= hour <= 8 or 18 <= hour <= 19:
            #if self.index == 0:
                #print("Entrou")
            return [exp_generator(0.2, 5)]
        else:
            return [exp_generator(0.6, 3)]

    def weekend_periodicy(self, clock):
        hour = clock.hour
        if 0 <= hour <= 5:
            return [exp_generator(1, 1)]
        elif 21 <= hour <= 23 or 6 <= hour <= 8:
            return [exp_generator(0.75, 1), exp_generator(1, 1)]
        else:
            return [exp_generator(0.6, 3)]
```

A matriz de transição associada é a mesma matriz dos dados com intervalo de 1 minuto pois não foi possível gerar a matriz de transição associada a estes dados.
