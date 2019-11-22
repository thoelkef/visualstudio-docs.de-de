---
title: Wie kann eine Zugriffsverletzung gedebuggt werden? | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.access
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f6188cc273cdea1755071e36f606fb8f041508d7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297315"
---
# <a name="how-can-i-debug-an-access-violation"></a>Wie kann eine Zugriffsverletzung gedebuggt werden?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Problembeschreibung  
 Das Programm generiert eine Zugriffsverletzung. Wie kann dieses Problem behoben werden?  
  
## <a name="solution"></a>Lösung  
 Wenn eine Zugriffsverletzung bei einer Codezeile auftritt, in der mehrere Zeiger dereferenziert werden, kann es schwierig sein, zu ermitteln, welcher Zeiger die Zugriffsverletzung verursacht hat. Ab Visual Studio 2015 Update 1 nennt das Ausnahmedialogfeld jetzt explizit den Zeiger, der die Zugriffsverletzung verursacht hat.  
  
 Beispielsweise sollte der folgende Code zu einer Zugriffsverletzung führen:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class ClassB {  
public:  
      ClassC* C;  
      ClassB() {  
            C = new ClassC();  
      }  
     void printHello() {  
            cout << "hello world";  
      }  
};  
  
class ClassA {  
public:  
    ClassB* B;  
    ClassA() {  
            B = nullptr;  
      }  
};  
  
int main() {  
    ClassA* A = new ClassA();  
    A->B->printHello();  
}  
```  
  
 Wenn Sie diesen Code in Visual Studio 2015 Update 1 ausführen, sollte das folgende Ausnahmedialogfeld angezeigt werden:  
  
 ![AccessViolationCPlus](../debugger/media/accessviolationcplus.png "AccessViolationCPlus")  
  
 Wenn Sie nicht bestimmen können, warum der Zeiger eine Zugriffsverletzung verursacht hat, überwachen Sie den Code mithilfe der Ablaufverfolgung, um sicherzustellen, dass der Zeiger, der das Problem verursacht, ordnungsgemäß zugewiesen wurde.  Wenn er als Parameter übergeben wird, achten Sie darauf, dass die Übergabe ordnungsgemäß erfolgt und Sie nicht versehentlich eine [flache Kopie](https://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy)erstellen. Überprüfen Sie anschließend, ob die Werte nicht unbeabsichtigt im Programm geändert werden, indem Sie einen Datenhaltepunkt für den fraglichen Zeiger erstellen, um sicherzustellen, dass er nicht an anderer Stelle im Programm geändert wird. Weitere Informationen zu Datenhaltepunkten finden Sie im Abschnitt über Datenhaltepunkte in [Using Breakpoints](../debugger/using-breakpoints.md).  
  
## <a name="see-also"></a>Siehe auch  
 [FAQs zum Debuggen von nativem Code](../debugger/debugging-native-code-faqs.md)
