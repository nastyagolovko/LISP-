# LISP-


#### ; 4. Определите функцию, порождающую по заданному натуральному числу N список, состоящий из натуральных чисел от 1 до N.

; Определяем функцию с именем "mylist" с одним входным параметром N, где N - заданное натуральное число

(defun mylist (n)

    ; В цикле for от 1 до N, где i - счетчик цикла, при каждой итерации цикла добавляем значение i в список
    ; collect накапливает первые N чисел в список
    
   (loop :for i :from 1 :to n :collect i))

; Проверка (просто вызываем функцию mylist с параметром 100 и печатаем ее вывод)

(write(mylist 100))



#### ; 2. Определите функцию, возвращающую последний q элемент списка.

; Определяем функцию с именем "q_element" с одним входным параметром q, где q - искомая позиция элемента в списке

(defun q_element (q)

	; Функции CAR и CDR служат для выделения головы и хвоста списка соответственно.
	; |Функция NTHCDR возвращает хвост списка, который будет получен путем вызова cdr n раз подряд.
	
   (car (nthcdr q x)))
; Проверка 
; Заведем переменную x и поместим туда нас список, например (a b c d)

(setq x '(a b c d))

; просто вызываем функцию q_element с параметром q и печатаем ее вывод 
; напечатает элемент A

(write (q_element 0))


#### ; 22. Определите функцию, которая обращает список (а b с) и разбивает его на уровни (((с) b) а).

(defun my_reverse_2 (L) 
 (cond 
  ((null L) nil) 
      ((null (cdr L)) L) 
          (T (list (my_reverse_2 (cdr L)) (car L))))) 

; Проверка 

(write (my_reverse '(а b с)))


#### ; 9. Определите функцию, разделяющую исходный список на два подсписка. В первый из них должны попасть элементы с нечетными номерами, во второй — элементы с четными номерами.

(defun 4et-ne4et (x)
  ; цикл с счетчиком i по всем элементам списка x
  (loop for i in x
		; если четный
        if (evenp i)
        ; то записываем этот элемент в список evens
        collect i into evens
        ; иначе записываем этот элемент в список odds
        else collect i into odds
        ; возвращаем эти списки
        finally (return (values evens odds))))
        
; проверка
(write (4et-ne4et '(1 2 2 3 10 8 4)))




#### ; 20. Определите функцию ПЕРВЫЙ-АТОМ, результатом которой будет первый атом списка. 
Пример:
; > (ПЕРВЫЙ-АТОМ '(((a b)) c d))
; A

(defun ПЕРВЫЙ-АТОМ (w)
  ; если список пустой, возвращаем nil
  (cond ((null w) nil)
		; функция listp - проверяет, является ли аргумент списком
		; если нет, то рекурсивно вызываем нашу функцию ПЕРВЫЙ-АТОМ и двигаемся дальше по списку
        ((listp (car w)) (ПЕРВЫЙ-АТОМ (car w)))
        ; иначе берем голову списка и вуаля
        ((car w))))
        
; проверка
(write (ПЕРВЫЙ-АТОМ '(((a b)) c d)))


#### ; 26. Определите функцию, разбивающую список (a b с d...) на пары ((а b) (с d)...).
; Определяем функцию с именем "пары" с одним входным параметром - списком
(defun пары (w)
   (cond ((null (cdr w) w)
            (t (cons (list (car w) (cadr w)) (пары (cddr w)))))))
        
; проверка
(write (пары '(a b c d)))


#### ; 28. Определите функцию, вычисляющую, сколько всего атомов в списке (списочной структуре).
; Определяем функцию с именем "сколько_атомов" с одним входным параметром - списком
(defun сколько_атомов (w)
	; если список пустой, то возвращаем ноль
    (if (null w)
        0
        ; иначе... как обычно, берем голову списка и если это атом, то
        ; увеличиваем "счетчик" на единичку и в конце возвращаем его
        ; и так далее... т.е. рекурсивно вызываем нашу функцию "сколько_атомов" для хвоста списка
        (+ (if (atom (car w)) 1 0) (сколько_атомов (cdr w)))))
    
; проверка
(write (сколько_атомов '(a b c d)))



#### 47. Определите функцию УДАЛИТЬ-ВСЕ-СВОЙСТВА, которая удаляет все свойств символа.		

(DEFUN УДАЛИТЬ-ВСЕ-СВОЙСТВА (SYMBOL)
  (COND ((NULL (SYMBOL-PLIST SYMBOL)) T)
        (T (REMPROP SYMBOL (CAR (SYMBOL-PLIST SYMBOL)))
         (УДАЛИТЬ-ВСЕ-СВОЙСТВА SYMBOL))))
