---
title: "__box | Microsoft Docs"
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
  - "__box"
  - "__box_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__box-Schlüsselwort"
  - "Boxing"
  - "Unboxing"
  - "Boxing __box-Schlüsselwort"
ms.assetid: 935b4a4d-fc45-484c-87c6-d95cfc67cc9d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __box
> [!NOTE]
>  Dieses Thema gilt nur für Version 1 von Managed Extensions für C\+\+. Diese Syntax sollte nur verwendet werden, um Code von Version 1 beizubehalten. Finden Sie unter [Boxing](/visual-cpp/windows/boxing-cpp-component-extensions) Informationen zur Verwendung der entsprechenden Funktionalität in der neuen Syntax.  
  
 Erstellt eine verwaltete Kopie eines \_\_value\-Klassenobjekts.  
  
## Syntax  
  
```  
  
__box(  
value-class identifier  
)  
  
```  
  
## Hinweise  
 Das Schlüsselwort `__box` wird verwendet, um ein verwaltetes Objekt \(abgeleitet von **System::ValueType**\) aus einem vorhandenen \_\_value\-Klassenobjekt zu erstellen. Wenn das `__box`\-Schlüsselwort auf eine \_\_value\-Klasse angewendet wird:  
  
-   Ein verwaltetes Objekt wird auf dem Common Language Runtime\-Heap zugeordnet.  
  
-   Der aktuelle Wert des \_\_value\-Klassenobjekts wird bitweise in das verwaltete Objekt kopiert.  
  
-   Die Adresse des neuen verwalteten Objekts wird zurückgegeben.  
  
 Dieser Prozess wird als Boxing bezeichnet. Dadurch kann jedes \_\_value\-Klassenobjekt in generischen Routinen verwendet werden, die für ein beliebiges verwaltetes Objekt funktionieren, da das verwaltete Objekt indirekt von **System::Object** erbt \(da **System::ValueType** von **System::Object** erbt\).  
  
> [!NOTE]
>  Das neu erstellte geschachtelte Objekt ist eine Kopie des \_\_value\-Klassenobjekts. Daher wirken sich Änderungen am Wert des geschachtelten Objekts nicht auf den Inhalt des \_\_value\-Klassenobjekts aus.  
  
## Beispiel  
 Hier sehen Sie ein Beispiel für Boxing und Unboxing:  
  
```  
// keyword__box.cpp  
// compile with: /clr:oldSyntax  
#using < mscorlib.dll >  
using namespace System;  
  
int main() {  
  Int32 i = 1;  
  System::Object* obj = __box(i);  
  Int32 j = *dynamic_cast<__box Int32*>(obj);  
}  
```  
  
 Im folgenden Beispiel wird ein nicht verwalteter Werttyp \(`V`\) geschachtelt und als verwalteter Parameter an die Funktion `Positive` übergeben.  
  
```  
// keyword__box2.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__value struct V {  
   int i;  
};  
void Positive(Object*) {}   // expects a managed class  
  
int main() {  
   V v={10};   // allocate and initialize  
   Console::WriteLine(v.i);  
  
   // copy to the common language runtime heap  
   __box V* pBoxedV = __box(v);  
   Positive(pBoxedV);   // treat as a managed class  
  
   pBoxedV->i = 20;   // update the boxed version  
   Console::WriteLine(pBoxedV->i);  
}  
```  
  
 **10 20**