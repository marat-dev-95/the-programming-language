как работает go:

сначало package
import 
func,vars,const, type порядок не имеет значения

точка с запятой только в случае если две или более интсрукции находятся на одной строке, можно но зачем

не должно быть так что открывающая фигурная скобка была но новой строке и можно переносить после + тоесть когда ожидается второй операнд

gofmt приводит код к стандартному формату,  а go fmt приводит весь пакет 

goimports автоматический решает пробелему удаления лишних библеотек с программы 

пакет os предоставляет функции и занчения для работы с операц системой платформо-независмомы образом. 
os.Args - аргументы переданные в командной строке начинается со 1 , 0 это название выполняемой программы

по соглашению мы описываем пакет до package name в коментарии

можно обьявлять переменную так var num int32 = 54 , либо   num := 54 то будет по умолчанию int, если переменная не инициализирвоана то будет значение по умолчанию
тоесть для числа это 0, для строки это "" 


i++ это не как в php  тоесть его нельзя присвоить в переменную,  используется как САМОСТОЯТЕЛЬНАЯ инструкия и не дожна идти вместе с другими в виде присвоения и тд

в go нет префиксных операторов таких как --i ++i и тд, по соображениям то что выше

go имеет единсветнный цикл for

for инициализация; условие; последсвтие {
	
}

инициализация является не обязательной 

любая из перчисленных частей может быть опущена,  при отстуствии условии и инициализации можно опустить точни с запятой

пустой идентификатор  для опущения значения

s := ""
var s string

var s = ""

var s string = ""

первый вариант может использован толька на уровне фукнции, второй вариант основан на инициализации по умолчанию , третья испоьзуется редко в основном при обьявлении нескольких переменных, четвертое это явное указание типа, нужно например если требуемый тип не совпадает с типом инициализатора

map это ссылка на структуру данных 

const (
	name = 0
)

могут быть как внутри функции так и на уровне пакета

значением может быть число, строка, либо булевое занчение

[]string{}, mysstruct{} - это составной литерал, комактная запись для инстанцирования составных типов GO, 



чтобы защиттиься от одновременному паралельному изменнеию переменной не согласованно используется mutex

можно в конструкции if инициализировать и проверить 

if init; condition {
	
}



switch variable {
	case "kek":

	etc
}

а может быть switch  {
	case kek>4 {

	}

	etc
}

иснтукции for, switch, select могут иметь метки на которые могут ссылаться continue, break


именнованные типы (struct)


в го есть указатели они содержать адреса переменных

в чем различие между укзаателем и ссылкой

когда мы создаем укзаатель мы присваеваем ему адрес памяти, тогда как ссылка являеется алтернативным имененм присваемой переменной

имена функции переменнтых констант типов меток паетов чувстиельны к регистру начинаться должны с буквы далле цифры бувы и символы подчеркивания

true, false, iota nil - константы 

int, string , error - это типы

функции make len cap new append copy close delete complex real imag panic recover

их можно переименовать 


имена пакетов состоят из строчных букв и без подчеркивании и camelcase

а имена фукнции camelCase

буквы сокращении такие как html, ascii не должны камелкейситься, тоесть escapeHtml а надо htmlEscape

переменные уровня пакета инициализуются до начало выполнения main

а локальные переменные инициализуруются тогда когда в процессе выполнения функции встречаются их обьявления

переменные могут быть инициализированы выражением(вызов функции, операция сложения ит д)

в функции для обьявления и инициализции локальных переменных может иоспльзваться кратие обьявления переменной

не обязательные в кратном обьявлении все левые переменные обьявляются,  если они уже были обьявлены то для них просто присваеваются

но краткое обьявление переменной должно обьвялять как миникм одну новую переменную 

краткое обьявление переменной дейтвует как присваевание только для переменных котые уже были обьвялены в том же лексическом блкое , обьвяления во внешнем блоке игнорируется 

переменная представляет сообой небольшой блок памяти, содержащий значение. и идентифицируются по имени , имя переменной считывает его значение за исклюяениям когда они находятся слева от присваевания


функция new(T)

создает новую именнованную переменную типа T, с нулевым значе нием и возвращает ее адрес , тоесть *T


две перменные тип которых не несет никакой инфораации а потому имеющие нулевой размер такие как stuct{} или [0]int могут иметь один и тотже адрес 

переменная живет до тех пор пока она доступна

если пути к переменной не существует то она очищается сборщиком


следующиие операторы могут в зависимости от случая возвращать два результата

v, ok = m[key]
v, ok = x.(T)\
v, ok = <-ch

значение nil может быть присвоено ссылочному типу или типу интерфейса

область видимости

заключенные в фигурных скопках переменные не видны снаружи

блок({}) определяет область видимости



В языке программирования Go "universe block" (или универсальный блок) — это понятие, которое относится к области видимости на самом высоком уровне, доступной в любом месте программы. В "universe block" определены предопределённые типы, значения и функции, которые являются встроенными и доступны в любом месте вашего кода без необходимости импорта или специального объявления.

Примеры элементов, которые находятся в "universe block":

Базовые типы данных, такие как int, float, string и bool.
Встроенные функции, такие как len, cap, make, new, append, copy и close.
Константы true, false и iota.
nil, специальное значение для указателей, слайсов, карт, каналов и функций, обозначающее "нет значения" или "нулевой".


на уровне пакета порядок обьявления не важен

типы в  GO

фундаментальные, составные, ссылочные , интерфейсы

фундматентальные:
числа строки булев

rune является синонимомом int32 и по соглашению укзаывет что данное значение является символом unicode. эти два имени могут использоваться взаимозаменяемо. 

аналогично тип byte является синонимом для типа uint8 и подчеркивает что это значение явлется фрагментом неформатированных данных, а не малым числом


byte = int8


int != 32 int != 64

знаковые числа представлены в формате дополнения до 2 в котором старшйй бит зарезервирован  для знака числа а диапазон значении n-разрядного простирается от -2(n-1) до 2(n-1) -1

тоесть 128 число вмещается в один байт , в один вмесщается знак

% применяется только в целым числам -5%2 = -2

поведение / зависит от того явлются ли его операнды целыми числами , так что 5.0/4.0 hfdyj 1.25
но 5/4 = 1

если результат арифметической операции имеет больше битов чем тип результата то это называется переполнением (overflow) и старшие биты которые не помещаются в резльутате молча отбразываются 


нельзя сравнивать значение разных типов

все фундаментальные типы лочические числа и строки являются сравниваемыми . 


TODO нужно поделать урпаженине с битовыми сдвигами 


почему len() возвращает int а не uint потому что при цикле в обратоном порядке был бы бесконечным


uint как правило используется редко,  когда побитовые операции или работа с бинарными файлами и тд

 для каждого типа T операция T(x) преобразует значение x в тип T если такое преобразование разрешено

 два вариана чисел с плавающей точкой float32 и float64

 точность float32 - 6 десятичных, float64 - 15десятичных

 макс значение float32 невелико - 16млн

 при присваевании можно опустить левое или правое значение в точоке

 строки представляют собой неизменяютмую последовательность байтов 

 len() возвращает кол-во байт в стоке 

 строку не изменить


 неизменяемость строки позволяет двум копиям строки безопасно раздлять одну и ту же память что делает копирование строки любой длинны очень дешевой операциией

 строковое значение можно запимсать как стркоовой литерал , опследовтаельность байтов, заключенную в двойные кавычки

 поскольку исходные файлы Go всегда спользуют кодировку UTF-8 а по соглашению тектсовые строки Go интерпритируеются как закодированные с использванем UTF-8  мы можем включать Unicode в строковые литералы

 в строки могут быть включены управляющие последовательнсоти с обратной чертой как \n и тд


можно строки быть с помощью одинарных обратных кавычек вместо двойных, внутри которого не обрабатываются управляющие последовтельнсти может состоять из несколькоиз строк исходного текста 


Unicode 

давным давно жизннь была простой и вней хватало по райнерй мене в США толко одного небольшого набора символов ASCII(American Standard Code for Information Interchange) который исоползьует 7 бит для представления 128 символов

прописных и строчных английски хбукв цифр и разнообразных снаков пунктуации и управляющих символов устройств. Но других странах не могли использовать свои писменности.  C ростом интернета данные на многочисленных яызках стали гораздо более распространенным явлением. Как рабоать со всем этим богатым материалом причем рабоатть эффективно? UNICODE

UNICODE в котором собраты все символы из всех мировых систем письменности плюс разнообразные символы ударении  и прочие диакритические знаки, управляющие коды наподобие символа табилацияя .  Каждому символу назначен стандарный номер - код символа Unicode или в терминологии Go - РУНА

Unicode - это стандарт 


utf8 - это кодировка символов unicode в виде байтов

старшые биты первого байта указывает сколько указывают сколко байтов следует за первым , нулевый старший байт указывает что это 7-битовый символ ASCII 

пакет unicode предоставляет функции для кодирования и декодирование рун в виде байтов с испоьзованием utf-8, и функции отличать бкуквы от цифр и проброзвать строчвые в прописные 

многие символы unicode трудно набрать на клаве или визуально отличить от других некоторые вообще не видны, управляющиая последовательность unicode в строковых литералах Go позволяют укзаывать символы Unicode  с помощью их чисолового кода . типа \uhhhh

для работы со строками важны 4 пакета: bytes, strings, strconv, unicode

посколько строки неизменяемы, инкрементное увеличение стркои может включать огромное кол-во выделение памяти и копировании. в таких случаях более эфееквными является исползовние bytes.Buffer

strconv позволяет преоброзовать булевые значение целых чисел и чисел с плавающе йточкой в строковое представление (и обратно). 

функции для классификации рун такие как isDigit, isLetter, isUpper, isLower в uniicode

такие же есть в strings только он применяет вышее для каждой руны


можно испоьзовать байтовый срез вместо стригна для изменения теущей строки 

чтобы из строки сделать байтовый срез нужно сделать следуещее

[]byte(s)

срез байтов содержит такие же методы как в strings

такие как 

bytes.Contains, Count, Field, Index, Join 


bytes предоставляет тип Buffer для эффективной работы со срезами байтов

изначально пуст  но растет по мере тго как в него записываются данные типов наподобие string, byte , []byte . 

buf.WriteByte('[')
buf.WriteString(", ")
его можно потом превратить в строку buf.String()

преоброзвание между стркоми и числами 

strconv

для число>строка можно использовать fmmt.Sprintf, алтернатива strconv.Itoa(integer to ASCII)

Константы 

выражения - значение которых известны компилятору и вычисление которых гарантированно происходит во время компиляции, а не вовремя выполнения.  может быть логическое числов или строка

синтаксический выглядит как переменная и предотврощает его изменнеие 

многие вычисления констант могут быть полностью завершены во время компляции уменьшая тем самым кол-во работ необхдимых во время выолпнения  .  при этом ошибки обычно обнаруиваемые во вермя выполнения могут быть найдены во время комплиции если операнды предсаляют собой константы наприер целочисленное деление на нуль 


константа может быть не привязана к типу , их точность гораздо выше чем фундаментальные типы а их аарифметика более точна, 


Составные типы

массив - последовательность фиксированной длинны из нуля или более элементов определенного типа. 

срезы - могут увеличиваться и уменьшаться более гибкие но чтобы понять срезы сначало следует разобраься с массивом

изначальное присваеваются нулевые значение типов элемента(для чисел этo 0 и тд). для иницализации массива списком значении можно испоьлзовать литерал массива

var q [3]int = [3]int{1,2,3}

если в литерале массива на месте длинны находистя ... то длинна массива определяется кол-во инициализаторов, 

q := [...]int{1,2,3}

размер массива явлеется частью типа [3]int != [4]int

синтаксис литерала для массива среза отображении(мапа) и структур подобен ({})

длинна массива определеяется наибольшим индексом при инициализаци

можно сравнить одинаковый типа массива 

при передаче в функции значение коируется в соответсующую переменную, в го массивы также преедаются и может жрать память , но можно передать указатель 

массивы копируются , структуры копируются

slice, map, chan, *T не копируются 

Срезы - последовтаельность переменной длинны , одного типа. 

Срез - это легковесная структура данных, которая предоставяет доступ к подпоследовательности элементов массива(или возможно ко всем элементам), известного как базовы массив

срез состоит из трех компотентов(указателя длинны и емкости)
указатель указывает на первый элемент массив, доступный через срез(который не обязательно совпдаает с первым элементом массива), Длина - это кол-во элементов среза, она может не превышать емкость, которая, как правило, представляет собой кол-во элементов между началом среза и концом базового массива. эти значение возвращатся встроенными функциями len и cap

несколько срезов могут совместно использовать один и тот же базовый массив и относиться к перекрывающимся частям этого массива. 

оператор среза s[i:j] создает новйы срез ссылающийся на элементы поселдовательности . это может быть массив указателем или другим срезом. 

start := []int{1,2,3,4,5}
first := start[0:2]
second := first[0:4]
выведет 1,2,3,4

срез содержит указатель на элемент массива, передача среза в функцию позволяет изменять элементы базового массива. 

когда создается срез автоматический создается массив и срез ссылается на него

срезу нельзя сравнивать == , вместо этого есть bytes.Equal

ключом в мапе не могут быть слайсы поскольку они изменяемы и один и тот же элемент может иметь разные значение в разное время

для ссылочных типов таких как указатели и каналы оператор == проверяет ссылочную тождественность тоесть ссылаются ли две сущности на один и тот же обьект,

Однако, когда вы добавляете элементы в слайс с помощью функции append, и если в результате этих операций требуется больше места, чем позволяет текущая вместимость (cap) слайса, Go автоматически выделяет новый участок памяти, который больше текущей вместимости, копирует туда существующие элементы и добавляет новые. В этот момент слайс перестаёт ссылаться на исходный массив start и начинает ссылаться на новый участок памяти.

Map 
хэш таблица. неупорядоченная коллекция пар ключ-зачение, в которой все ключи различны а занчение связанное с заданным ключом можно получить обовить или удалить с испоьзвоинем в среднем константного кол-во сравнении ключей. независимо от размера хэш таблица.

в go мап представляет собой ссылку на хэш таблицу, а тип отображения записывается как map[K]V, где K и V являются типами его клювей и значении.   Тип ключей должен быть сраниым оператораомо ==, чтобы мапа могло проверить равен ли данный ключ одному из имеющихся в нем. 

map можно создать с помощью make

ages := make(map[string]int) алтернатива map[string]int{}

для создания + инициализации

ages := map[string]int{
	"alice": 31,
}

удаление с помощью dleete(ages, "key")

операции все безопасны, при исползвании ключа которого нет будет нелвоев значение соответсщуего типа. 

однаком элементы мапа не являются переменными и мы не можем получить их адреса &ages["alice"]

одна из причин это то что с ростом мапы может быть повторное хэширование элементов в новые места хранения, что потенцильно делает адреса не действительными. 

сохранение значении в нулевый мап приведет к ошибке 

var ages map[string]int

ages["carol"] = 21

перед тем как выполнять примсываенвание следует выделить память для отображеню

можно чекать есть ли жлемент в мапе с так

if age, ok := ages["blob"]; !ok {}

map нельзя сравнивать друг с другом


Структура представляет собой агрегированый тип данных обьеденяющий нуль или более именованных значении произовольных типов в единое целое. Каждое знаение называется полем. 


var dilbert Employee

dilbert.Salary -= 5000

position := &dilbert.Position

*position = "Senior " + *position 

запись с точкой работает и с указателями на структуры

var employeeOfTheMonth *Employee = &dilbert

employeeOfTheMonth.Position += " (активный учатсник команды)"

(*employeeOfTheMonth).Position += " (активный участник команды)"

 можно на результат функции применять поля

 тоесть EmployeeById(dilbert.ManagerID).Position


 если EmployeeById возвращает не укзатаель 
 то выражение EmployeeById(33).Salary = 0 вызовет ошибку посколлько левая часть не укзаывает на переменную

 последовательность одного и того же типа могут быть обьеденены

 type Employee struct {
 	ID int, 
 	Name, Address string
 }

 порядок полей имеет важное значение для идентификации типа.  
 если поменять местами Adress  и Name то это уже другой тип структуры. обычно обьеденяются толко связанные поля

структурный тип может иметь поле такого же типа только с указателем во избежания рекурсии

нулевое значение для структуры состоит из нелувых занчении кажогоо из ее полей 

занчение может быть записано в порядке обьявления тоесть

type Positn struct { X, Y int}

p:=Point{1,2}

в одном и том же литерале нльзя смшеивать именованное и поярдоковое писвоение


Автоматическое разыменовывание 

Go упрощает работу с полями структур через указатели, автоматически разыменовывая их при доступе к полям. Это означает, что вам не нужно явно разыменовывать указатель при обращении к полям структуры:

go
(*pp).X = 3 // Явное разыменование указателя, не требуется
pp.X = 3    // Go автоматически разыменовывает pp при доступе к X

если все поля структуы сравниваемы то сама структура сравниваема, сравнивается каждое поле с соответстующим. 

сравниваемые типы структур могут быть ключами в мапе

Go позволяет обьявить поле с типом но без имени, такие поля называются анонимные полями. Тип поля должен представлять собой именнованный тип или указатель на именованный тип

мы говорим что тип Point ввстроен в другой тип (embedded)

тоессть допустим есть 

type Point struct {
	x, y int
}

type Cicle struct {
	Point,
	Radius int
}

при этом можно общращаться как Cicly.Point.x так и опустить Point и общращаться Cicle.x

при этом мы не можем общараться так 

w = Cicle {
	x: 3, y: 3, Radis: 3
}

он должен следовать обьвлениею в Cicle 

тоесть w = Cicle {
	Point {1,2},
	Radus: 3
}

может помочь при выводе структуры

fmt.Printf("%#v\n", w)

не может быть двух ананоимных полей однакого типа


именнованный тип ????????



JSON

го может превосходно работать с декодированием и кодированием json с помощью пакета ecoding/json

JSON -эфеективное удобочитаемое представление фудаментальных типов данных: числа,  логическе значения, и строки которые прдеставляют собой последовабетльности симвоолов unicode

массивы в json - массивы в го и срезы

обьекты в json - map и struct

преобразование структуры данных Go наподобие movies в JSON называется МАРШАЛИНГОМ . json.Marshal:

data, err := json.Marshal(movies)

if err != nil {
	log.Fatalf("Сбой маршалинга")
} 


Marshal генерирует байтовый срез, содержащий очень длинную строку без лишних прбелов, здесь мы разорвали эту строку, чтобы она поместилась на тсраницах книги. 

чтобы было удобно читать можно использовать MarshalIndent

`json:"released"` - дескриптор полей в структуре

в Go есть шаблонизаторы text/template html/template


Функции

параметр - это при обьявлении функции
аргумент - это конкретное значение которое передается функции

при именованном результате он создает локальную перменную и инициализируется нуелвым занчением 

если возвращаеттся несколько значении должно быть return Если только исполнение явно не может дойти до конца функции 

параметры или результаты могут тип один раз записываться 

сигнатуры функции совпадают если типы параметров и типы резльутатов совпадает , названия не важны

встроенный тип error является типом интерфейса. 

причина по которой Go не использует исключения заключается в том что исключения как правило смешивают опасиние ошибки с обирабатывающим потмоокм управления 

ошибки обычно конкотенироуется в стеке, и поэтому ненужно начинать с прописных букв и новой строкки, 

defer отложенный вызов, гарантирует что он будет выполнен после завершении функции или авраинного выхода

Каналы

мозволяют из одной горутины передавать данные в другую

каждый канал явлетс сресвтам передачи занчении определенного типа который называется типом элементов канала

канал явлется ссылкой на структуру данных нулевое значение является nil

канал имеет две основные операции отправление и полчение, вместе известные как коммуникации (communications). в инстукции отправление <- разделяет канал и значение тоесть chan <- val

в выражние получение <- предшестует операнду канала

x = <- ch 

каналы поддерживают опреаццию закрытия которая устанавливает флаг указывающий что по этому каналу больше не будут передаваться значения; после этого любые оппытки отправления завершаются аварииной ситауциией. операции поучения значение к закрытому каналу приводят к получению значение которые были отправлены ранее до тез пр пока полученных значении не останется . любые дальнейшие попытки получить значеня приводят к немедленому завершению операции  и возврату нелевого занчение типа эелмента канала

чтобы закрыть канал используется функция close 
close(ch)

канал созданные с помощью просто вызова make(chan int) называется небуферизованным каналом, но make принимает второй аргумент целое занчеие которое называется емакосью канаала. если емкость канала ненулевая мейк созданет буферизованный канал

 Небуферизованные каналы

 операция оптравение в небуферизоанный канал блокирует горутину до тех пор пока другая го программа не выолнит соответсвующее получение зи того же канала, после чего значение становится переданным и обе горутины продожаются. и наборот если первой сделана оппытка выполнить поерацию получения принмающая горутина блокируется до тех пор пока другая го программа не выполнит отпраление значения в тот же канал. 

 связь по небуферизированному каналу приводит к синхронизации операции отправления и получения. 


 существует проверка на получение значение из закрытого канала это

 x, ok := <-naturals

 if !ok {
 	//закрыт
 }

 из-за распространенности ситауции  и некуклюжесоти выше синатктсиса язык позволяет использовать для получение всех занчении из канала цикл по диапазону. это болуу удобный синтаксис дляполучение всех значении, отправленных в канал, и завершения работы после получения последнего элемента

 вам не нужно закрытваь каждйы канал по завершении работы с ним. неободимо закрывать каналы тогда когда важно сообщить принмающей горутине что все данные уже оптравлены. 

 попытка закртыть уже закрытый канал вызывает авариную ситауцию также как и закрытие нелувого канала. 

 для предотвращение неверного применения система типов го предостовляет тип однонаправленного канала который обеспечивыает только одну операцию - отправление или получение. Тип chan<-int представляет собой канал int, предназначенный толкьо для оптравления, который позволяет отправлять данне но не полуать их  напротив тип <- chan int  канал инт предназначенниый толко для получения 


 если изначально канал двунаправленный его можно сделать однонаправленным в параметре функции но не наоборот


Буферизированный канал

опреация отправления в буферизированный канал вставляет элемент в конец оечерди а операция получения удаляетпервый элемент из очереди. Если канал заполнен опреация отправления блокриует свою горутину до тех пор пока другая горутина не освободит место получив данные из канаала. и наоборот если канал пуст опреация получения блокиреут го подпрограмму до тог оомента опка канал не будет послано занчене из другой горутины

в канал можно оптравлить без блокировки по размеру канала

когда необхдиомо знать емкость буфера канала ее можно получить вызвав cpa(ch)


len(ch) возвращает кол-во элементов находящизся в настощяее время в буфере. 

ненужно использваоть каналы как очередь, лучше использовать срезы


для циклов полезно делать вейт группы счетчиков

sync.WaitGroup 

Add()

Don()

wg.Wait()

