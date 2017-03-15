---
title: "__property | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__property_cpp"
  - "__property"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__property-Schlüsselwort"
  - "Verwaltete Klassen"
  - "Eigenschaften [C++], verwaltete Klassen"
ms.assetid: 235e3574-6882-4c52-8301-270277b9216d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __property
> [!NOTE]
>  Dieses Thema gilt nur für Version 1 von Managed Extensions für C\+\+. Diese Syntax sollte nur verwendet werden, um Code von Version 1 beizubehalten. Finden Sie unter [property](/visual-cpp/windows/property-cpp-component-extensions) Informationen zur Verwendung der entsprechenden Funktionalität in der neuen Syntax.  
  
 Deklariert entweder einen Skalar oder eine indizierte Eigenschaft für die verwaltete Klasse.  
  
## Syntax  
  
```  
  
__property  
function-declarator  
  
```  
  
## Hinweise  
 Das `__property`\-Schlüsselwort stellt die Deklaration einer Eigenschaft vor und kann in einer Klasse, einer Schnittstelle oder einem Werttyp angezeigt werden. Eine Eigenschaft kann über eine Getter\-Funktion \(schreibgeschützt\), eine Setter\-Funktion \(lesegeschützt\) oder beide \(Lese\-\/Schreibzugriff\) verfügen.  
  
> [!NOTE]
>  Ein Eigenschaftenname kann nicht mit dem Namen der verwalteten Klasse übereinstimmen, in der er enthalten ist. Der Rückgabetyp der Getter\-Funktion muss dem Typ des letzten Parameters einer entsprechenden Setter\-Funktion entsprechen.  
  
## Beispiel  
 Im folgenden Beispiel wird eine skalare Eigenschaft \(`Size`\) zur `MyClass`\-Deklaration hinzugefügt. Die Eigenschaft wird dann implizit festgelegt und mithilfe der `get_Size`\- und `set_Size`\-Funktionen abgerufen:  
  
```  
// keyword__property.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__gc class MyClass {  
public:  
   MyClass() : m_size(0) {}  
   __property int get_Size() { return m_size; }  
   __property void set_Size(int value) { m_size = value; }  
   // compiler generates pseudo data member called Size  
protected:  
   int m_size;  
};  
  
int main() {  
   MyClass* class1 = new MyClass;  
   int curValue;  
  
   Console::WriteLine(class1->Size);  
  
   class1->Size = 4;   // calls the set_Size function with value==4  
   Console::WriteLine(class1->Size);  
  
   curValue = class1->Size;   // calls the get_Size function  
   Console::WriteLine(curValue);  
}  
```  
  
## Ausgabe  
  
```  
0  
4  
4  
```