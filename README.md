# Лабораторная работа № 1: Интерполяция в условиях измерений с неопределенностью

## Базовая часть:

  1. Разработать функцию `qubic_spline_coeff(x_nodes, y_nodes)`, которая посредством решения матричного уравнения вычисляет коэффициенты естественного кубического сплайна.
  2. Написать функции `qubic_spline(x, x_nodes, qs_coeff)` и `d_qubic_spline(x, x_nodes, qs_coeff)`, которые вычисляют соответственно значение кубического сплайна и его производной в точке `x` (`qs_coeff` обозначает матрицу коэффициентов).
  3. Используя данные в таблице 1, требуется построить аппроксимацию зависимости уровня поверхности жидкости h(x) от координаты x (рис. 1) с помощью кубического сплайна и продемонстрировать ее на графике вместе с исходными узлами.

![title1](рис1.png)

Рисунок 1. Поверхность вязкой жидкости (серая кривая), движущейся сквозь некоторую среду (например, пористую). Её значения известнытолько в нескольких точках (красные узлы)

Таблица 1: Значения уровня поверхности вязкой жидкости

|  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | 
| `x_i` | 0.0 | 0.1 | 0.2 | 0.3 | 0.4 | 0.5 | 0.6 | 0.7 | 0.8 | 0.9 | 1.0 |
| `h_i` | 3.37 | 3.95 | 3.73 | 3.59 | 3.15 | 3.15 | 3.05 | 3.86 | 3.60 | 3.70 | 3.02 |

## Продвинутая часть:

  1. Разработать функцию `l_i(i, x, x_nodes)`, которая возвращает значение i-го базисного полинома Лагранжа, заданного на узлах с абсциссами `x_nodes`, в точке `x`.
  2. Написать функцию `L(x, x_nodes, y_nodes)`, которая возвращает значение интерполяционного полинома Лагранжа, заданного на узлах с абсциссами `x_nodes` и ординатами `y_nodes`, в точке $x$.
  3.  Известно, что при измерении координаты `x` всегда возникает погрешность, которая моделируется случайной величиной с нормальным распределением с нулевым математическим ожиданием и стандартным отклонением $10^{-2}$. Требуется провести следующий анализ, позволяющий выявить влияние этой погрешности на интерполяцию. Сгенерировать 1000  векторов значений $[ \tilde x_1,..., \tilde x_{11}]^T$ предполагая, что $\tilde x_i = x_i + Z$, где $x_i$ соответствует значению в таблице 1 и $Z$ является случайной величиной с нормальным распределением с нулевым математическим ожиданием и стандартным отклонением $10^{-2}$. Для каждого из полученных векторов построить интерполянт Лагранжа, предполагая, что в качестве абсцисс узлов используются значения $\tilde x_i$, а ординат -- $h_i$ из таблицы 1. В результате вы должны иметь 1000 различных интерполянтов. Предполагая, что все интерполянты представляют собой равновероятные события, построить такие функции $\tilde h_l(x)$ и $\tilde h_u(x)$, где $\tilde h_l(x) < \tilde h_u(x) \ \forall x \in [0, 1]$, что вероятность того, что значение интерполянта в точке будет лежать в интервале $[\tilde h_l(x) , \  \tilde h_u(x)]$, равна 0.9. Отобразить на едином графике функции $h_l(x), \ h_u(x)$, усредненный интерполянт и узлы из таблицы 1. Какие участки интерполянта и почему являются наиболее чувствительными к погрешностям?
    
  4. Повторить анализ, описанный в предыдущем пункте, в предположении, что координаты $x_i$ вам известны точно, в то время как измерения уровня поверхности $h_i$ имеют ту же погрешность, что и в предыдущем пункте. Изменились ли выводы вашего анализа?
  5. Повторить два предыдущие пункта для случая интерполяции кубическим сплайном. Какие выводы вы можете сделать, сравнив результаты анализа для интерполяции Лагранжа и интерполяции кубическим сплайном?

## Результаты

Расположены в директории `hw1`: в файле `comp_math_lab1.ipynb` находится код с комментариями, в файле `educmm_lab_2021_rk6_52b_gorelkinaee_lab1.pdf` находится подробный отчет о проделланой работе.
