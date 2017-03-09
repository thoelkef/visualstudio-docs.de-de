---
title: "Compilerfehler beim Implementieren einer von CObject abgeleiteten Klasse | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Kompilieren von Quellcode, von CObject abgeleitete Klassen"
  - "Fehler [C++]"
  - "Fehler [C++], Compiler"
  - "CObject-Klasse, Compilerfehler für abgeleitete Klassen"
ms.assetid: 9f249b52-aeff-41a1-8a74-a52aa08c4fcf
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Compilerfehler beim Implementieren einer von CObject abgeleiteten Klasse
Wenn Sie eine von `CObject` abgeleitete Klasse implementieren und Ihr Code so geschrieben ist, dass der Kopierkonstruktor oder Zuweisungsoperator für die Klasse aufgerufen werden muss, meldet der Compiler möglicherweise Fehler wie die folgenden:  
  
```  
error C2660: 'CSample::CSample' : function does not take 1 parameters error C2582: 'CSample' : 'operator =' function is unavailable  
```  
  
 Sie können das Problem reproduzieren, indem Sie das Beispiel im folgenden Abschnitt mit dem Beispielcode kompilieren.  
  
> [!NOTE]
>  Mit dem Beispielcode in diesem Artikel werden folgende Fehlermeldungen generiert:  
  
```  
error C2558: 'CSample::CSample' : no copy constructor available error C2582: 'CSample' : 'operator =' function is unavailable  
```  
  
 Die Compilerfehler sind darauf zurückzuführen, dass `CObject` einen privaten Kopierkonstruktor und Zuweisungsoperator in der Datei "AFX.h" deklariert. Das bedeutet, dass der Compiler keinen standardmäßigen Kopierkonstruktor und Zuweisungsoperator für die von `CObject` abgeleitete Klasse generiert. Da der Compiler in der Klasse die deklarierten Funktionen nicht finden kann, werden die Fehler gemeldet.  
  
 Um die Compilerfehler zu vermeiden, müssen Sie einen Kopierkonstruktor und Zuweisungsoperator für die von `CObject` abgeleitete Klasse implementieren. Dies wird im folgenden Beispielcode verdeutlicht. Sie können die Fehler vermeiden, indem Sie die im Beispielcode angegebenen Zeilen auskommentieren.  
  
## Beispielcode  
  
```  
// _error_Compiler_Errors_when_Implementing_a_CObject.2d.Derived_Class.cpp /* Compile options needed: /c */ // replace with #define _CONSOLE when compiling for Windows NT #define _DOS #include <afx.h> class CSample : public CObject { private: short m_nValue; public: // uncomment the lines below to avoid the compiler errors //    CSample() {} //    CSample( const CSample &s )  // copy ctor //        { m_nValue = s.m_nValue; } //    CSample& operator=( const CSample &s )  // assignment operator //        { m_nValue = s.m_nValue; return *this; } }; int main() { CSample a; CSample b = a; a = b; }  
  
```  
  
## Siehe auch  
 [Compilerwarnungs C4600 Through C4999](/visual-cpp/error-messages/compiler-warnings/compiler-warnings-c4600-through-c4799)