---
title: "Vorgehensweise: Erstellen eines Typs, der NULL-Werte zulässt (Klassen-Designer) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- nullable types, Class Designer
- Class Designer [Visual Studio], nullable types
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
caps.latest.revision: 11
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 001e8d8c1a6371d76b1a52826da16d471f07c1ba
ms.contentlocale: de-de
ms.lasthandoff: 05/30/2017

---
# <a name="how-to-create-a-nullable-type-class-designer"></a>Gewusst wie: Erstellen eines Typs, der Nullwerte zulässt (Klassen-Designer)
Bestimmte Werttypen verfügen nicht immer über einen definierten Wert oder benötigen keinen. Dies ist in Datenbanken üblich, in denen möglicherweise einigen Feldern kein Wert zugewiesen wird. Sie können z.B. einem Datenbankfeld einen NULL-Wert zuweisen, um zu zeigen, dass noch kein Wert zugewiesen wurde.  
  
 Ein *Nullable-Typ* ist ein Werttyp, den Sie erweitern, sodass der normale Wertebereich für diesen Typ als auch ein NULL-Wert benötigt werden. Ein Nullable von `Int32`, auch bezeichnet als Nullable\<Int32>, kann beispielsweise einem Wert im Bereich von -2147483648 bis 2147483647 oder einem NULL-Wert zugewiesen werden. Einem Nullable\<bool> können die Werte `True`, `False`, oder NULL (überhaupt kein Wert) zugewiesen werden.  
  
 Auf NULL festlegbare Typen sind Instanzen der <xref:System.Nullable%601>-Struktur. Jede Instanz eines Nullable-Typs hat zwei öffentliche schreibgeschützte Eigenschaften `HasValue` und `Value`:  
  
-   `HasValue` ist vom Typ `bool` und gibt an, ob die Variable einen definierten Wert enthält. `True` bedeutet, dass die Variable einen nicht-NULL-Wert enthält. Sie können mithilfe einer Anweisung wie `if (x.HasValue)` oder `if (y != null)` auf einen definierten Wert testen.  
  
-   `Value` hat denselben Typ wie der zugrunde liegende Typ. Wenn `HasValue` `True` ist, enthält `Value` einen sinnvollen Wert. Wenn `HasValue` `False` ist, wird der Zugriff auf `Value` eine ungültige Operationsausnahme auslösen.  
  
 Beim Deklarieren einer Variablen als Nullable-Typ verfügt sie standardmäßig über keinen definierten Wert (`HasValue` ist `False`) als der Standardwert des ihr zugrunde liegenden Werttyps.  
  
 Der Klassen-Designer zeigt einen Nullable-Typ so an wie den zugrunde liegenden Typ.  
  
 Weitere Informationen zu Typen in Visual C# finden Sie unter [Typen, die NULL-Werte zulassen](/dotnet/csharp/programming-guide/nullable-types/index). Weitere Informationen zu Nullable-Typen in Visual Basic finden Sie unter [Auf NULL festlegbare Werttypen](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-add-a-nullable-type-by-using-the-class-designer"></a>Hinzufügen eines Nullable-Typs mithilfe des Klassen-Designers  
  
1.  Im Klassendiagramm erweitern Sie eine vorhandene Klasse, oder erstellen eine neue Klasse.  
  
2.  Klicken Sie im Menü **Klassendiagramm** auf **Hinzufügen** und anschließend auf **Klasse hinzufügen**, um dem Projekt eine Klasse hinzuzufügen.  
  
3.  Klicken Sie im Menü **Klassendiagramm** auf **Erweitern**, um die Klassenform zu erweitern.  
  
4.  Wählen Sie die Klassenform aus. Klicken Sie im Menü **Klassendiagramm** auf **Hinzufügen** und anschließend auf **Feld**. Ein neues Feld mit den Standardnamen **Feld** wird in der Klassenform und auch im Fenster **Klassendetails** angezeigt.  
  
5.  Ändern Sie in der Spalte **Name** im Fenster **Klassendetails** (oder in der Klassenform selbst) den Namen des neuen Felds in einen gültigen und aussagekräftigen Namen.  
  
6.  Deklarieren Sie in der Spalte **Typ** im Fenster **Klassendetails** den Typ als Nullable-Typ, wie im folgenden Code gezeigt:  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
### <a name="to-add-a-nullable-type-by-using-the-code-editor"></a>Hinzufügen eines Nullable-Typs mithilfe des Code-Editors  
  
1.  Fügen Sie dem Projekt eine Klasse hinzu. Wählen Sie im **Projektmappen-Explorer** einen Projektknoten aus und klicken Sie dann im Menü **Projekt** auf **Klasse hinzufügen**.  
  
2.  Fügen Sie in der CS- oder VB-Datei für die neue Klasse eine oder mehrere Nullable-Typen in der Klassendeklaration hinzu.  
  
3.  Ziehen Sie das Klassensymbol in der Klassenansicht zur Entwurfsoberfläche des Klassen-Designers. Eine Klassenform wird im Klassendiagramm angezeigt.  
  
4.  Erweitern Sie die Details für die Klassenform, und bewegen Sie den Mauszeiger über die Klassenmember. Die QuickInfo zeigt die Deklaration der einzelnen Member.  
  
5.  Klicken Sie mit der rechten Maustaste auf Klassenform und auf **Klassendetails**. Sie können die Eigenschaften des neuen Typs im Fenster **Klassendetails** anzeigen oder ändern.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Nullable%601>   
 [Typen, die NULL-Werte zulassen](/dotnet/csharp/programming-guide/nullable-types/index)   
 [Verwenden von auf NULL festlegbaren Typen](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)   
 [Vorgehensweise: Identifizieren eines Typs, der NULL-Werte zulässt](/dotnet/csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type)   
 [Auf NULL festlegbare Werttypen](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)
