---
title: Debuggen einer C++-Zugriffsverletzung | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 02/05/2019
ms.topic: how-to
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 803f81d1a26438c2134349a85369d341353e17cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350419"
---
# <a name="how-can-i-debug-a-c-access-violation"></a>Wie erfolgt das Debuggen einer C++-Zugriffsverletzung?

## <a name="problem-description"></a>Problembeschreibung

Das Programm generiert eine Zugriffsverletzung. Wie kann dieses Problem behoben werden?

## <a name="solution"></a>Lösung

Wenn eine Zugriffsverletzung bei einer Codezeile auftritt, in der mehrere Zeiger dereferenziert werden, kann es schwierig sein, zu ermitteln, welcher Zeiger die Zugriffsverletzung verursacht hat. Ab Visual Studio 2015 Update 1 nennt das Ausnahmedialogfeld jetzt explizit den Zeiger, der die Zugriffsverletzung verursacht hat.

Beispielsweise sollte der folgende Code zu einer Zugriffsverletzung führen:

```C++
#include <iostream>
using namespace std;

class ClassC {
public:
  void printHello() {
    cout << "hello world";
  }
};

class ClassB {
public:
  ClassC* C;
  ClassB() {
    C = new ClassC();
  }
};

class ClassA {
public:
  ClassB* B;
  ClassA() {
    // Uncomment to fix
    // B = new ClassB();
  }
};

int main() {
  ClassA* A = new ClassA();
  A->B->C->printHello();

}
```

Wenn Sie diesen Code in Visual Studio 2015 Update 1 ausführen, sollte das folgende Ausnahmedialogfeld angezeigt werden:

![AccessViolationCPlus](../debugger/media/accessviolationcplus.png "AccessViolationCPlus")

Wenn Sie nicht bestimmen können, warum der Zeiger eine Zugriffsverletzung verursacht hat, überwachen Sie den Code mithilfe der Ablaufverfolgung, um sicherzustellen, dass der Zeiger, der das Problem verursacht, ordnungsgemäß zugewiesen wurde.  Wenn er als Parameter übergeben wird, achten Sie darauf, dass die Übergabe ordnungsgemäß erfolgt und Sie nicht versehentlich eine [flache Kopie](https://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy) erstellen. Vergewissern Sie sich anschließend, dass die Werte nicht unbeabsichtigt im Programm geändert werden. Erstellen Sie zu diesem Zweck einen Datenhaltepunkt für den fraglichen Zeiger. So sorgen Sie dafür, dass er nicht an anderer Stelle im Programm geändert wird. Weitere Informationen zu Datenhaltepunkten finden Sie im Abschnitt über Datenhaltepunkte in [Using Breakpoints](../debugger/using-breakpoints.md).

## <a name="see-also"></a>Siehe auch
- [FAQs zum Debuggen von nativem Code](../debugger/debugging-native-code-faqs.md)