{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Задача нелинейный метод найменьших квадратов"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Математический метод, применяемый для решения различных задач, основанный на минимизации суммы квадратов отклонений некоторых функций от искомых переменных. Он может использоваться для «решения» переопределенных систем уравнений (когда количество уравнений превышает количество неизвестных), для поиска решения в случае обычных (не переопределенных) нелинейных систем уравнений, для аппроксимации точечных значений некоторой функции. МНК является одним из базовых методов регрессионного анализа для оценки неизвестных параметров регрессионных моделей по выборочным данным"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Импортируем библиотеку:"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "import matplotlib.pyplot as plt"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Она отвечает за отрисовку графика, мы назовем ее plt, также импортируем:"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "import matplotlib as mpl"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Нужно импортировать библиотеку numpy"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "import numpy as np"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Назовем ее np, с помощью неё будем аппроксимировать данные методом наименьших квадратов."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Ниже представленны входные значения точек x и y исходящих из условия задачи для дальнейшего решение метода наимешьних квадратов."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "x=[2.5134, 2.0443, 1.6684, 1.3664, 1.1232, 0.9269, 0.7679, 0.6389, 0.5338, 0.4479, 0.3776, 0.3197, 0.2720, 0.2325, 0.1997, 0.1723, 0.1493, 0.1301, 0.1138, 0.1,0.0883,0.0783,0.0698,0.0624] \n",
    "y=[0, 0.05, 0.1, 0.15, 0.2, 0.25, 0.3, 0.35, 0.4, 0.45,\n",
    "   0.5, 0.55, 0.6, 0.65, 0.7, 0.75, 0.8, 0.85, 0.9, 0.95,1,1.05,1.1,1.15]"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Создадим функцию mnkGP:"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "def mnkGP(x,y):"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "В функции создадим переменную d, она будет отвечать за степень полинома."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "d= 0.99"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Дальше с помощью np.polyfit(),аппроксимируем данные методом наименьших квадратов."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "beta = np.polyfit(x,y,d)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Выведем на экран коэффициент:"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "print('Коэффициент -- a %s  '%round(beta[0],4))"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "beta0 = beta"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Отрисуем исходный график:"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "plt.plot(x, y, 'o', label='Original data', markersize=5)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Сгенерируем данные на основе значений из списка x."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "xx = np.linspace(x[23], x[0], 24)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Отрисуем график:"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "plt.plot(x, beta0*xx)\n",
    "plt.legend()\n",
    "plt.grid()\n",
    "plt.show()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Дальше мы вызовим нашу функцию и передадим ей значения x и y:"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "mnkGP(x,y)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Запустим наш скрипт на Python и посмотрим вывод на графике:"
   ]
  },
 
   
   },
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "![Figure_1.png](attachment:Figure_1.png)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Вывод"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Мы смогли решить систему уравнений с помощью метода найменьших квадратов и вывести график на экран. Результаты не отличаются высокой точностью, но при этом являются достаточно объективными"
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.7.6"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 4
}
