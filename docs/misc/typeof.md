---
title: "__typeof | Microsoft Docs"
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
  - "__typeof_cpp"
  - "__typeof"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__typeof-Schlüsselwort"
ms.assetid: d71b9603-35d0-4c62-b5b4-90ffc2305a55
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __typeof
**Hinweis** Dieses Thema gilt nur für Version 1 von Managed Extensions für C\+\+. Diese Syntax sollte nur verwendet werden, um Code von Version 1 beizubehalten. Finden Sie unter [typeid](/visual-cpp/windows/typeid-cpp-component-extensions) Informationen zur Verwendung der entsprechenden Funktionalität in der neuen Syntax.  
  
 Gibt den **Systemtyp** \(System::Type\) eines angegebenen Typs zurück.  
  
```  
  
__typeof(  
typename  
)  
  
```  
  
 Dabei gilt:  
  
 *typename*  
 Der Name eines verwalteten Typs, für den der **System::Type**\-Name erforderlich ist. Beachten Sie, dass bei manchen systemeigenen Typen in einem verwalteten Programm ein Aliasing zu Typen in der Common Language Runtime vorgenommen wird. Beispielsweise ist `int` ein Alias für **System::Int32**.  
  
## Hinweise  
 Mit dem **\_\_typeof**\-Operator können Sie den **System::Type**\-Typ eines Typs abrufen, den Sie angeben.**\_\_typeof** kann auch verwendet werden, um einen Wert aus **System::Type** in einem benutzerdefinierten Attributblock zurückzugeben. Weitere Informationen zum Erstellen Ihrer eigenen Attribute finden Sie unter [Attribut](/visual-cpp/windows/attribute).  
  
## Beispiel  
 Im folgenden Beispiel wird ein benutzerdefiniertes Attribut \(`AtClass`\) auf eine \_\_gc\-Klasse \(`B`\) angewendet. Der Wert des benutzerdefinierten Attributs wird dann mit **\_\_typeof** abgerufen:  
  
```  
// keyword__typeof.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
public __gc class MyClass {};  
  
[attribute(All)]  
__gc class AtClass {  
public:  
   AtClass(Type*) {  
      Console::WriteLine("in Type * constructor");  
   }  
  
   AtClass(String*) {}  
   AtClass(int) {}  
};  
  
[AtClass(__typeof(MyClass))]   // Apply AtClass attribute to class B  
__gc class B {};  
  
int main() {  
   Type * mytype = __typeof(B);  
   Object * myobject __gc[] = mytype -> GetCustomAttributes(true);  
   Console::WriteLine(myobject[0]);  
}  
```  
  
## Ausgabe  
  
```  
in Type * constructor  
AtClass  
```