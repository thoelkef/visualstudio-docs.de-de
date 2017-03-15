---
title: "__delegate | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__delegate_cpp"
  - "__delegate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Delegaten _delegate-Schlüsselwort"
  - "verwalteten Funktionszeigern"
  - "__delegate-Schlüsselwort"
ms.assetid: a41d2211-b79b-4509-a4c2-cc91f3d4fc9d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __delegate
**Hinweis** Dieses Thema gilt nur für Version 1 von Managed Extensions für C\+\+. Diese Syntax sollte nur verwendet werden, um Code von Version 1 beizubehalten. Finden Sie unter [delegate](/visual-cpp/windows/delegate-cpp-component-extensions) Informationen zur Verwendung der entsprechenden Funktionalität in der neuen Syntax.  
  
 Definiert einen Referenztyp, der verwendet werden kann, um eine Methode mit einer bestimmten Signatur zu kapseln.  
  
## Syntax  
  
```  
  
__delegate   
function-declarator  
  
```  
  
## Hinweise  
 Ein Delegat entspricht mit Ausnahme des folgenden Unterschieds ungefähr einem Funktionszeiger in C\+\+:  
  
-   Ein Delegat kann an eine oder mehrere Methoden innerhalb einer \_\_gc\-Klasse gebunden werden.  
  
 Wenn der Compiler auf das `__delegate`\-Schlüsselwort trifft, wird eine Definition einer \_\_gc\-Klasse generiert. Dieser \_\_gc\-Klasse weist folgende Merkmale auf:  
  
-   Es erbt von **System::MulticastDelegate**.  
  
-   Er verfügt über einen Konstruktor, der zwei Argumente akzeptiert: einen Zeiger auf eine \_\_gc\-Klasse oder **NULL** \(im Fall der Bindung an eine statische Methode\) und eine vollständig qualifizierte Methode des angegebenen Typs.  
  
-   Er verfügt über eine Methode mit dem Namen `Invoke`, deren Signatur der deklarierten Signatur des Delegaten entspricht.  
  
## Beispiel  
 Im folgenden Beispiel werden eine \_\_gc\-Klasse \(`MyCalendar`\) und ein Delegat \(`GetDayOfWeek`\) deklariert. Der Delegat wird anschließend an die verschiedenen Methoden von `MyCalendar` gebunden und ruft alle nacheinander auf:  
  
```  
// keyword__delegate.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__delegate int GetDayOfWeek();  
__gc class MyCalendar {  
public:  
   MyCalendar() : m_nDayOfWeek(4) {}  
   int MyGetDayOfWeek() {   
      Console::WriteLine("handler"); return m_nDayOfWeek;   
   }  
   static int MyStaticGetDayOfWeek() {   
      Console::WriteLine("static handler");   
      return 6;  
   }  
private:  
   int m_nDayOfWeek;  
};  
  
int main () {  
   GetDayOfWeek * pGetDayOfWeek;  // declare delegate type  
   int nDayOfWeek;  
  
   // bind delegate to static method  
   pGetDayOfWeek = new GetDayOfWeek(0, &MyCalendar::MyStaticGetDayOfWeek);  
   nDayOfWeek = pGetDayOfWeek->Invoke();  
   Console::WriteLine(nDayOfWeek);  
  
   // bind delegate to instance method  
   MyCalendar * pcal = new MyCalendar();  
   pGetDayOfWeek = static_cast<GetDayOfWeek*>(Delegate::Combine(pGetDayOfWeek,  
      new GetDayOfWeek(pcal, &MyCalendar::MyGetDayOfWeek)));  
   nDayOfWeek = pGetDayOfWeek->Invoke();  
   Console::WriteLine(nDayOfWeek);  
  
   // delegate now bound to two methods; remove instance method  
   pGetDayOfWeek = static_cast<GetDayOfWeek*>(Delegate::Remove(pGetDayOfWeek,  
      new GetDayOfWeek(pcal, &MyCalendar::MyGetDayOfWeek)));  
}  
```  
  
## Beispielausgabe  
  
```  
static handler  
6  
static handler  
handler  
4  
```