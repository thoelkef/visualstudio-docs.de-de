---
title: "Compilerfehler CS0313 | Microsoft Docs"
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
  - "CS0313"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0313"
ms.assetid: a0b0f2fb-e742-4df8-98bd-3bc068f0c71c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0313
Der Typ "type1" kann nicht als Typparameter "parameter name" im generischen Typ oder in der generischen Methode "type2" verwendet werden. Der Typ "type1", der NULL\-Werte zulässt, entspricht nicht der Einschränkung von "type2". Typen, die NULL\-Werte zulassen, können Schnittstelleneinschränkungen nicht entsprechen.  
  
 Ein Typ, der NULL\-Werte zulässt, entspricht nicht dem zugehörigen Typ, der nicht auf NULL festgelegt werden kann. Im folgenden Beispiel entspricht `ImplStruct` der `BaseInterface`\-Einschränkung, `ImplStruct?` hingegen nicht, da `Nullable<ImplStruct>` nicht `BaseInterface` implementiert.  
  
### So beheben Sie diesen Fehler  
  
1.  Bei Verwendung des folgenden Codes als Beispiel besteht eine Lösung darin, eine normale `ImplStruct` als erstes Typargument im Aufruf der `TestMethod` zu verwenden. Bearbeiten Sie dann die `TestMethod`, um eine Version der `Implstruct` in der zugehörigen Rückgabeanweisung zu erstellen, die Nullwerte zulässt:  
  
    ```  
    return new Nullable<T>(t);  
    ```  
  
## Beispiel  
 Durch den folgenden Code wird der Fehler CS0313 ausgelöst:  
  
```  
// cs0313.cs public interface BaseInterface { } public struct ImplStruct : BaseInterface { } public class TestClass { public T? TestMethod<T, U>(T t) where T : struct, U { return t; } } public class NullableTest { public static void Run() { TestClass tc = new TestClass(); tc.TestMethod<ImplStruct?, BaseInterface>(new ImplStruct?()); // CS0313 } public static void Main() { } }  
```  
  
## Siehe auch  
 [Typen, die NULL\-Werte zulassen](/dotnet/csharp/programming-guide/nullable-types/index)