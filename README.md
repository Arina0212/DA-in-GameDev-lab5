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
```
![image](https://user-images.githubusercontent.com/114181560/205019212-65af9247-84bd-45c6-8c4f-daf0e335ce55.png)

Установилa TensorBoard. Перейдя по выведенной ссылке получила следующие графики:

![1](https://user-images.githubusercontent.com/114181560/205024781-cdec15c7-2483-4c42-8d71-8b1d529f1d98.png)

# Задание №2
Далее буду изменять какие-либо параметры файла Economic.yaml. Задача - добиться максимальной монотонности и линейности графика Cumulative Reward.

Изменил batch_size с 1024 на 2000. Занаво запустила обучение. И получила новые графики.

![2](https://user-images.githubusercontent.com/114181560/205024813-97dc013d-7b58-4121-841b-ceea33cb2515.png)

График стал всегда равен 1.


Изменила batch_size с 1024 на 300. 

![3](https://user-images.githubusercontent.com/114181560/205024894-f67c371a-cf6b-4de4-bf43-332b91e3aa91.png)

График стал более кривым.


Вернула batch_size 1024, изменила lambd с 0.95 на 0.9

![4](https://user-images.githubusercontent.com/114181560/205024958-c0e2d8b0-ecce-4ca2-a9f6-723165611c77.png)


график стал более линеен.
Г


## Выводы
