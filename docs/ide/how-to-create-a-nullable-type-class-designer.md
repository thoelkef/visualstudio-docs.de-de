---
title: "How to: Create a Nullable Type (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "nullable types, Class Designer"
  - "Class Designer [Visual Studio], nullable types"
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Create a Nullable Type (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bestimmte Werttypen haben \(bzw. benötigen\) nicht immer einen definierten Wert.  Dies ist in Datenbanken üblich, in denen einigen Feldern möglicherweise kein Wert zugewiesen wurde.  Beispielsweise können Sie einem Datenbankfeld einen NULL\-Wert zuweisen, um anzugeben, dass ihm noch kein Wert zugewiesen wurde.  
  
 Ein *Typ, der NULL\-Werte zulässt* ist ein Wertetyp, den Sie erweitern, damit er den typischen Wertebereich für diesen Typ sowie einen NULL\-Wert akzeptiert.  Dem auf NULL festlegbaren Typ `Int32`, der auch als Nullable\<Int32\> bezeichnet wird, kann beispielsweise ein Wert von \-2147483648 bis 2147483647 oder ein NULL\-Wert zugewiesen werden.  Einem \<bool\>\-Typ, der NULL\-Werte zulässt, können die Werte `True`, `False` oder NULL \(überhaupt kein Wert\) zugewiesen werden.  
  
 Typen, die NULL\-Werte zulassen, sind Instanzen der <xref:System.Nullable%601>\-Struktur.  Jede Instanz eines Typs, der NULL\-Werte zulässt, verfügt über zwei öffentliche schreibgeschützte Eigenschaften: `HasValue` und `Value`:  
  
-   `HasValue` hat den Typ `bool` und gibt an, ob die Variable einen definierten Wert enthält.  `True` bedeutet, dass die Variable einen Wert ungleich NULL enthält.  Mithilfe einer Anweisung wie `if (x.HasValue)` oder `if (y != null)` können Sie überprüfen, ob ein definierter Wert vorliegt.  
  
-   `Value` hat denselben Typ wie der zugrunde liegende Typ.  Wenn `HasValue` den Wert `True` hat, enthält `Value` einen sinnvollen Wert.  Wenn `HasValue` den Wert `False` hat, wird durch den Zugriff auf `Value` eine Ausnahme über einen ungültige Operation ausgelöst.  
  
 Wenn Sie eine Variable als Typ deklarieren, der NULL\-Werte zulässt, weist sie anders als der Standardwert des ihr zugrunde liegenden Werttyps keinen definierten Wert auf \(`HasValue` hat den Wert `False`\).  
  
 Der Klassen\-Designer zeigt einen Typ, der NULL\-Werte zulässt, auf dieselbe Weise an wie dessen zugrunde liegenden Typ.  
  
 Weitere Informationen über Typen, die NULL\-Werte zulassen, in Visual C\# finden Sie unter [Typen, die NULL\-Werte zulassen](/dotnet/csharp/programming-guide/nullable-types/index).  Weitere Informationen über Typen, die NULL\-Werte zulassen, in Visual Basic finden Sie unter [Nullable Value Types](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### So fügen Sie einen Typ, der NULL\-Werte zulässt, mithilfe des Klassen\-Designers hinzu  
  
1.  Erweitern Sie im Klassendiagramm eine vorhandene Klasse, oder erstellen Sie eine neue Klasse.  
  
2.  Um einem Projekt eine Klasse hinzuzufügen, klicken Sie im Menü **Klassendiagramm** auf **Hinzufügen** und dann auf **Klasse hinzufügen**.  
  
3.  Um die Klassenform im Menü **Klassendiagramm** zu erweitern, klicken Sie auf **Erweitern**.  
  
4.  Wählen Sie die Klassenform aus.  Klicken Sie im Menü **Klassendiagramm** auf **Hinzufügen** und dann auf **Feld**.  Ein neues Feld, das über den Standardnamen **Feld** verfügt, wird in der Klassenform und im Fenster **Klassendetails** angezeigt.  
  
5.  Ändern Sie in der Spalte **Name** des Fensters **Klassendetails** \(oder in der Klassenform selbst\) den Namen des neuen Feldes in einen gültigen und aussagekräftigen Namen.  
  
6.  Deklarieren Sie in der Spalte **Typ** des Fensters **Klassendetails** den Typ als auf NULL festlegbaren Typ, wie im folgenden Code dargestellt:  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
### So fügen Sie einen Typ, der NULL\-Werte zulässt, mithilfe des Code\-Editors hinzu  
  
1.  Fügen Sie dem Projekt eine Klasse hinzu.  Wählen Sie den Projektknoten im **Projektmappen\-Explorer** aus, und klicken Sie dann im Menü **Projekt** auf **Klasse hinzufügen**.  
  
2.  Fügen Sie der Klassendeklaration in der CS\- oder VB\-Datei für die neue Klasse mindestens einen Typ, der NULL\-Werte zulässt, hinzu.  
  
3.  Ziehen Sie das Symbol für eine neue Klasse aus der Klassenansicht auf die Entwurfsoberfläche des Klassen\-Designers.  Eine Klassenform wird im Klassendiagramm angezeigt.  
  
4.  Erweitern Sie die Details für die Klassenform, und bewegen Sie den Mauszeiger über die Klassenmember.  In einer QuickInfo wird die Deklaration der einzelnen Member angezeigt.  
  
5.  Klicken Sie mit der rechten Maustaste auf die Klassenform, und klicken Sie auf **Klassendetails**.  Sie können die Eigenschaften des neuen Typs im Fenster **Klassendetails** anzeigen lassen oder ändern.  
  
## Siehe auch  
 <xref:System.Nullable%601>   
 [Typen, die NULL\-Werte zulassen](/dotnet/csharp/programming-guide/nullable-types/index)   
 [Verwenden von auf NULL festlegbaren Typen](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)   
 [Gewusst wie: Identifizieren eines Typs, der NULL\-Werte zulässt](../Topic/How%20to:%20Identify%20a%20Nullable%20Type%20\(C%23%20Programming%20Guide\).md)   
 [Nullable Value Types](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)