# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
## Интеграция экономической системы в проект Unity и обучение ML-Agent
Отчет по лабораторной работе #5 выполнил(а):
- Шубина Арина Николаевна
- РИ-210947

Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 2.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 3.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Выводы.
- ✨Magic ✨

## Цель работы
познакомиться с перцептроном
## Постановка задачи.
В данной лабораторной работе мы в проекте Unity рализуем перцептрон, который умеет производить вычисления: OR, AND, NAND, XOR. Так же построим графики зависимости количества эпох от ошибки обучения. 


## Задание 1
Измените параметры файла. yaml-агента и определить какие параметры и 
как влияют на обучение модели.
Файл Economic.yaml
```py
behaviors:
  Economic:
    trainer_type: ppo
    hyperparameters:
      batch_size: 1024
      buffer_size: 10240
      learning_rate: 3.0e-4
      learning_rate_schedule: linear
      beta: 1.0e-2
      epsilon: 0.2
      lambd: 0.95
      num_epoch: 3      
    network_settings:
      normalize: false
      hidden_units: 128
      num_layers: 2
    reward_signals:
      extrinsic:
        gamma: 0.99
        strength: 2.0
    checkpoint_interval: 500000
    max_steps: 750000
    time_horizon: 64
    summary_freq: 5000
    self_play:
      save_steps: 20000
      team_change: 100000
      swap_steps: 10000
      play_against_latest_model_ratio: 0.5
      window: 10
``'
![image](https://user-images.githubusercontent.com/114181560/205019212-65af9247-84bd-45c6-8c4f-daf0e335ce55.png)
Установилa TensorBoard. Перейдя по выведенной ссылке выведенной получила следующие графики:

![image](https://user-images.githubusercontent.com/114181560/205023662-8364ad40-2f53-45db-bb96-a00c5bff637e.png)
# Задание №2


Далее буду изменять 5 раз какие-либо параметры файла Economic.yaml. Задача - добиться максимальной монотонности и линейности графика Cumulative Reward.

Изменил batch_size с 1024 на 2000. Занаво запустила обучение. И получила новые графики.

![image](https://user-images.githubusercontent.com/114181560/205019412-0e69b4c7-4d8f-4116-8467-35314e01167e.png)

График стал всегда равен 1.

Изменила batch_size с 1024 на 300. 

![image](https://user-images.githubusercontent.com/114181560/205019494-ac9ecd7b-8716-48f0-98f0-49052aa3f051.png)

График стал более кривым.

Вернула batch_size 1024, изменила lambd с 0.95 на 0.9

![image](https://user-images.githubusercontent.com/114181560/205019532-11d4e370-ff11-4a2a-8291-6f331bcdce4e.png)

график стал более линеен.
Оставила lambd 0.9 и изменила epsilon с 0.2 на 0.1

![image](https://user-images.githubusercontent.com/114181560/205019589-58d55fd4-a64f-43f0-a670-36bb097effdd.png)

Практически нет изменений.

Изменила num_epoch с 3 на 1.

![image](https://user-images.githubusercontent.com/114181560/205019637-23b7702c-093c-4e5a-ab07-4d34a27ce4e7.png)

Практически нет изменений.




## Выводы
