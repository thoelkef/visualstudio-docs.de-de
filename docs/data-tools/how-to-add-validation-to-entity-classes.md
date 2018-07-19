---
title: 'Gewusst wie: Hinzufügen von Validierungen zu Entitätsklassen'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d102bdf20349d6bd4efdecd1c460f1e46646eb37
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089337"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Gewusst wie: Hinzufügen von Validierungen zu Entitätsklassen
*Überprüfen von* Entitätsklassen wird bestätigt, die in Datenobjekte eingegebenen Werte mit den Einschränkungen in das Schema eines Objekts und den Regeln für die Anwendung zu erfüllen. Es dient der Fehlervermeidung, Daten vor dem Senden von Aktualisierungen an zugrunde liegende Datenbanken auf Gültigkeit zu überprüfen. Dadurch wird auch die potenzielle Anzahl von Roundtrips zwischen einer Anwendung und der Datenbank verringert.

 Die [LINQ to SQL-tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) stellt partielle Methoden, mit denen Benutzer, den vom Designer generierten Code zu erweitern, der ausgeführt wird, während Einfüge-, Update- und gelöscht werden, von Entitäten, die abgeschlossen und auch während und nach der einzelnen Spalte ändert.

> [!NOTE]
>  Dieses Thema enthält die grundlegenden Schritte zum Hinzufügen von Validierungen zu Entitätsklassen mit dem **O/R Designer**. Da es schwierig, diese generischen Schritte ohne Verweis auf eine bestimmte Entitätsklasse nachzuvollziehen sein könnte, wird eine exemplarische Vorgehensweise mit tatsächlichen Daten bereitgestellt.

## <a name="add-validation-for-changes-to-the-value-in-a-specific-column"></a>Hinzufügen von Validierung für Änderungen auf den Wert in einer bestimmten Spalte
 Dieses Verfahren veranschaulicht, wie Daten auf Gültigkeit geprüft werden, wenn sich der Wert in einer Spalte ändert. Da die Überprüfung, in der Klassendefinition ausgeführt wird (nicht in der Benutzeroberfläche), eine Ausnahme wird ausgelöst, wenn der Wert bewirkt, dass die Validierung fehlschlägt. Implementieren Sie eine Fehlerbehandlung für den Code in der Anwendung, der die Änderung von Spaltenwerten durchführt.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-validate-data-during-a-columns-value-change"></a>So validieren Sie Daten während einer Änderung eines Spaltenwerts

1.  Öffnen oder erstellen Sie eine neue LINQ to SQL-Klassendatei (**dbml** Datei) in der **O/R Designer**. (Doppelklicken Sie auf die **dbml** Datei **Projektmappen-Explorer**.)

2.  In der **O/R Designer**, mit der rechten Maustaste in der Klasse, die für die Sie zum Hinzufügen von Validierungen, und klicken Sie dann auf möchten **Ansichtscode**.

     Der Code-Editor wird mit einer partiellen Klasse für die ausgewählte Entitätsklasse geöffnet.

3.  Platzieren Sie den Cursor in der partiellen Klasse.

4.  Für Visual Basic-Projekte:

    1.  Erweitern Sie die **Methodenname** Liste.

    2.  Suchen Sie die **OnCOLUMNNAMEChanging** Methode für die Spalte, der Sie Validierung hinzufügen möchten.

    3.  Ein `OnCOLUMNNAMEChanging` Methode wird der partiellen Klasse hinzugefügt.

    4.  Fügen Sie den folgenden Code hinzu, um zunächst zu überprüfen, ob ein Wert eingegeben wurde, und dann sicherzustellen, dass der für die Spalte eingegebene Wert für die Anwendung gültig ist. Das `value`-Argument enthält den vorgeschlagenen Wert, fügen Sie daher Logik hinzu, um sicherzustellen, das es sich um einen gültigen Wert handelt:

        ```vb
        If value.HasValue Then
            ' Add code to ensure that the value is acceptable.
            ' If value < 1 Then
            '    Throw New Exception("Invalid data!")
            ' End If
        End If
        ```

    Für C#-Projekte:

    Da c#-Projekten-Ereignishandler nicht automatisch generieren, können Sie IntelliSense verwenden, um die partiellen Methoden zur Änderung der Spalte zu erstellen. Geben Sie `partial` und dann ein Leerzeichen ein, um auf die Liste der verfügbaren partiellen Methoden zuzugreifen. Klicken Sie auf die Methode zur Spaltenänderung für die Spalte, der Sie Validierung hinzufügen möchten. Der folgende Code ähnelt den Code, der generiert wird, wenn Sie eine partielle Methode zur spaltenänderung auswählen:

    ```csharp
    partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
        {
           throw new System.NotImplementedException();
        }
    ```

## <a name="add-validation-for-updates-to-an-entity-class"></a>Hinzufügen von Validierungen für Updates zu einer Entitätsklasse
 Neben der Überprüfung von Werten während Änderungen können Sie auch Daten auf Gültigkeit prüfen, wenn versucht wird, eine vollständige Entitätsklasse zu aktualisieren. Validierung während eines versuchten Updates ermöglicht Ihnen, Werte in mehreren Spalten zu vergleichen, wenn die Geschäftsregeln dies erfordern. Das folgende Verfahren veranschaulicht die Validierung beim Versuch, eine vollständige Entitätsklasse zu aktualisieren.

> [!NOTE]
>  Der Validierungscode für Updates vollständiger Entitätsklassen wird in der partiellen <xref:System.Data.Linq.DataContext>-Klasse ausgeführt (statt in der partiellen Klasse einer bestimmten Entitätsklasse).

### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>So validieren Sie Daten während eines Updates einer Entitätsklasse

1.  Öffnen oder erstellen Sie eine neue LINQ to SQL-Klassendatei (**dbml** Datei) in der **O/R Designer**. (Doppelklicken Sie auf die **dbml** Datei **Projektmappen-Explorer**.)

2.  Mit der rechten Maustaste eines leeren Bereichs auf die **O/R Designer** , und klicken Sie auf **Ansichtscode**.

     Der Code-Editor wird mit einer partiellen Klasse für den `DataContext` geöffnet.

3.  Platzieren Sie den Cursor in die partielle Klasse für den `DataContext`.

4.  Für Visual Basic-Projekte:

    1.  Erweitern Sie die **Methodenname** Liste.

    2.  Klicken Sie auf **UpdateENTITYCLASSNAME**.

    3.  Ein `UpdateENTITYCLASSNAME` Methode wird der partiellen Klasse hinzugefügt.

    4.  Greifen Sie auf die Werte einzelner Spalten mithilfe des `instance`-Arguments zu, wie im folgenden Code dargestellt:

        ```vb
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
            Dim ErrorMessage As String = "Invalid data!"
            Throw New Exception(ErrorMessage)
        End If
        ```

    Für C#-Projekte:

    Da c#-Projekten-Ereignishandler nicht automatisch generieren, können Sie IntelliSense verwenden, um die partielle erstellen `UpdateCLASSNAME` Methode. Geben Sie `partial` und dann ein Leerzeichen ein, um auf die Liste der verfügbaren partiellen Methoden zuzugreifen. Klicken Sie auf die Updatemethode für die Klasse, die auf der Sie Validierung hinzufügen möchten. Der folgende Code ähnelt dem Code, der generiert wird, bei der Auswahl einer `UpdateCLASSNAME` partielle Methode:

    ```csharp
    partial void UpdateCLASSNAME(CLASSNAME instance)
    {
        if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))
        {
            string ErrorMessage = "Invalid data!";
            throw new System.Exception(ErrorMessage);
        }
    }
    ```

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Überprüfen von Daten](../data-tools/validate-data-in-datasets.md)
- [LINQ to SQL ((.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)