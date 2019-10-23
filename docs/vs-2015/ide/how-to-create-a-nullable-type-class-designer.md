---
title: 'Vorgehensweise: Erstellen eines Typs, der NULL-Werte zulässt (Klassen-Designer) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- nullable types, Class Designer
- Class Designer [Visual Studio], nullable types
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 438f84a172c7e0a2d0dc957c578adc568a46495f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668160"
---
# <a name="how-to-create-a-nullable-type-class-designer"></a>Vorgehensweise: Erstellen eines Typs, der NULL-Werte zulässt (Klassen-Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bestimmte Werttypen verfügen nicht immer über einen definierten Wert oder benötigen keinen. Dies ist in Datenbanken üblich, in denen möglicherweise einigen Feldern kein Wert zugewiesen wird. Sie können z.B. einem Datenbankfeld einen NULL-Wert zuweisen, um zu zeigen, dass noch kein Wert zugewiesen wurde.

 Ein *Nullable-Typ* ist ein Werttyp, den Sie erweitern, sodass der normale Wertebereich für diesen Typ als auch ein NULL-Wert benötigt werden. Ein Nullable von `Int32`, auch bezeichnet als Nullable\<Int32>, kann beispielsweise einem Wert im Bereich von -2147483648 bis 2147483647 oder einem NULL-Wert zugewiesen werden. Einem Nullable\<bool> können die Werte `True`, `False`, oder NULL (überhaupt kein Wert) zugewiesen werden.

 Auf NULL festlegbare Typen sind Instanzen der <xref:System.Nullable%601>-Struktur. Jede Instanz eines Nullable-Typs hat zwei öffentliche schreibgeschützte Eigenschaften `HasValue` und `Value`:

- `HasValue` ist vom Typ `bool` und gibt an, ob die Variable einen definierten Wert enthält. `True` bedeutet, dass die Variable einen nicht-NULL-Wert enthält. Sie können mithilfe einer Anweisung wie `if (x.HasValue)` oder `if (y != null)` auf einen definierten Wert testen.

- `Value` hat denselben Typ wie der zugrunde liegende Typ. Wenn `HasValue` `True` ist, enthält `Value` einen sinnvollen Wert. Wenn `HasValue` `False` ist, wird der Zugriff auf `Value` eine ungültige Operationsausnahme auslösen.

  Beim Deklarieren einer Variablen als Nullable-Typ verfügt sie standardmäßig über keinen definierten Wert (`HasValue` ist `False`) als der Standardwert des ihr zugrunde liegenden Werttyps.

  Der Klassen-Designer zeigt einen Nullable-Typ so an wie den zugrunde liegenden Typ.

  Weitere Informationen zu Typen in Visual C# finden Sie unter [Typen, die NULL-Werte zulassen](https://msdn.microsoft.com/library/e473cb01-28ca-42be-9cea-f717055d72c6). Weitere Informationen zu Nullable-Typen in Visual Basic finden Sie unter [Auf NULL festlegbare Werttypen](https://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6).

  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-add-a-nullable-type-by-using-the-class-designer"></a>Hinzufügen eines Nullable-Typs mithilfe des Klassen-Designers

1. Im Klassendiagramm erweitern Sie eine vorhandene Klasse, oder erstellen eine neue Klasse.

2. Klicken Sie im Menü **Klassendiagramm** auf **Hinzufügen** und anschließend auf **Klasse hinzufügen**, um dem Projekt eine Klasse hinzuzufügen.

3. Klicken Sie im Menü **Klassendiagramm** auf **Erweitern**, um die Klassenform zu erweitern.

4. Wählen Sie die Klassenform aus. Klicken Sie im Menü **Klassendiagramm** auf **Hinzufügen** und anschließend auf **Feld**. Ein neues Feld mit den Standardnamen **Feld** wird in der Klassenform und auch im Fenster **Klassendetails** angezeigt.

5. Ändern Sie in der Spalte **Name** im Fenster **Klassendetails** (oder in der Klassenform selbst) den Namen des neuen Felds in einen gültigen und aussagekräftigen Namen.

6. Deklarieren Sie in der Spalte **Typ** im Fenster **Klassendetails** den Typ als Nullable-Typ, wie im folgenden Code gezeigt:

    ```csharp
    // Declare a nullable type in Visual C#:
    class Test
    {
       int? building_number = 5;
    }
    ```

    ```vb
    ' Declare a nullable type in Visual Basic:
    Class Test
       Dim buildingNumber As Nullable(Of Integer) = 5
    End Class
    ```

### <a name="to-add-a-nullable-type-by-using-the-code-editor"></a>Hinzufügen eines Nullable-Typs mithilfe des Code-Editors

1. Fügen Sie dem Projekt eine Klasse hinzu. Wählen Sie im **Projektmappen-Explorer** einen Projektknoten aus und klicken Sie dann im Menü **Projekt** auf **Klasse hinzufügen**.

2. Fügen Sie in der CS- oder VB-Datei für die neue Klasse eine oder mehrere Nullable-Typen in der Klassendeklaration hinzu.

3. Ziehen Sie das Klassensymbol in der Klassenansicht zur Entwurfsoberfläche des Klassen-Designers. Eine Klassenform wird im Klassendiagramm angezeigt.

4. Erweitern Sie die Details für die Klassenform, und bewegen Sie den Mauszeiger über die Klassenmember. Die QuickInfo zeigt die Deklaration der einzelnen Member.

5. Klicken Sie mit der rechten Maustaste auf Klassenform und auf **Klassendetails**. Sie können die Eigenschaften des neuen Typs im Fenster **Klassendetails** anzeigen oder ändern.

## <a name="see-also"></a>Siehe auch
 [Typen](https://msdn.microsoft.com/library/e473cb01-28ca-42be-9cea-f717055d72c6) , die NULL-Werte zulassen, <xref:System.Nullable%601> Typen, die [Nullwerte](https://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28) zulassen [How Identifizieren eines Typs, der NULL-Werte zulässt ](https://msdn.microsoft.com/library/d4b67ee2-66e8-40c1-ae9d-545d32c71387)- [Werttypen](https://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6)
