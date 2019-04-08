---
title: 'Vorgehensweise: Hinzufügen von Validierungen zu Entitätsklassen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f3c08dbb66e71cc1fd362279ae33006c20e11436
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957684"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Vorgehensweise: Hinzufügen von Validierungen zu Entitätsklassen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Durch den Vorgang der *Validierung* von Entitätsklassen wird bestätigt, dass die in Datenobjekte eingegebenen Werte den Einschränkungen eines Objektschemas oder den bestehenden Regeln für die Anwendung entsprechen. Es dient der Fehlervermeidung, Daten vor dem Senden von Aktualisierungen an zugrunde liegende Datenbanken auf Gültigkeit zu überprüfen. Dadurch wird auch die potenzielle Anzahl von Roundtrips zwischen einer Anwendung und der Datenbank verringert.  
  
 Die [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) stellt partielle Methoden, mit denen Benutzer, den vom Designer generierten Code zu erweitern, der ausgeführt wird, während Einfüge-, Update- und gelöscht werden, von Entitäten, die abgeschlossen und auch während und nach der einzelnen Spalte ändert.  
  
> [!NOTE]
>  Dieses Thema beschreibt die grundlegenden Schritte zum Hinzufügen von Validierungen zu Entitätsklassen mit dem [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Da es schwierig sein könnte, diese generischen Schritte ohne Verweis auf eine bestimmte Entitätsklasse nachzuvollziehen, wird eine exemplarische Vorgehensweise mit tatsächlichen Daten zur Verfügung gestellt.  
  
## <a name="adding-validation-for-changes-to-the-value-in-a-specific-column"></a>Hinzufügen von Validierungen bei Werteänderungen in einer bestimmten Spalte  
 Dieses Verfahren veranschaulicht, wie Daten auf Gültigkeit geprüft werden, wenn sich der Wert in einer Spalte ändert. Da die Validierung innerhalb der Klassendefinition (nicht der Benutzeroberfläche) ausgeführt wird, wird eine Ausnahme ausgelöst, wenn die Validierung aufgrund des Werts fehlschlägt. Implementieren Sie eine Fehlerbehandlung für den Code in der Anwendung, der die Änderung von Spaltenwerten durchführt.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-validate-data-during-a-columns-value-change"></a>So validieren Sie Daten während einer Änderung eines Spaltenwerts  
  
1. Öffnen oder erstellen Sie eine neue LINQ to SQL-Klassendatei (**dbml** Datei) in der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Doppelklicken Sie im **Projektmappen-Explorer** auf die **DBML**-Datei.)  
  
2. In den O/R-Designer, mit der Maustaste der Klasse, die für das Hinzufügen von Validierungen, und klicken Sie dann auf werden sollen **Ansichtscode**.  
  
    Der Code-Editor wird mit einer partiellen Klasse für die ausgewählte Entitätsklasse geöffnet.  
  
3. Platzieren Sie den Cursor in der partiellen Klasse.  
  
4. Für Visual Basic-Projekte:  
  
   1. Erweitern Sie die Liste **Methodenname**.  
  
   2. Suchen Sie die **auf**_COLUMNNAME_**Changing** Methode für die Spalte, der Sie Validierung hinzufügen möchten.  
  
   3. Ein `On` *COLUMNNAME* `Changing` Methode wird der partiellen Klasse hinzugefügt.  
  
   4. Fügen Sie den folgenden Code hinzu, um zunächst zu überprüfen, ob ein Wert eingegeben wurde, und dann sicherzustellen, dass der für die Spalte eingegebene Wert für die Anwendung gültig ist. Das `value`-Argument enthält den vorgeschlagenen Wert, fügen Sie daher Logik hinzu, um sicherzustellen, das es sich um einen gültigen Wert handelt:  
  
      ```vb  
      If value.HasValue Then  
          ' Add code to ensure that the value is acceptable.  
          ' If value < 1 Then  
          '    Throw New Exception("Invalid data!")  
          ' End If  
      End If  
      ```  
  
      Für C#-Projekte:  
  
   5. Da C#-Projekte die Ereignishandler nicht automatisch generieren, können Sie IntelliSense verwenden, um die partiellen Methoden für die Spaltenänderung zu erstellen.  
  
       Geben Sie `partial` und dann ein Leerzeichen ein, um auf die Liste der verfügbaren partiellen Methoden zuzugreifen. Klicken Sie auf die Methode zur Spaltenänderung für die Spalte, der Sie Validierung hinzufügen möchten. Der folgende Code ähnelt dem Code, der generiert wird, wenn Sie eine partielle Methode zur Spaltenänderung auswählen:  
  
      ```csharp  
      partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)  
          {  
             throw new System.NotImplementedException();  
          }  
  
      ```  
  
## <a name="adding-validation-for-updates-to-an-entity-class"></a>Hinzufügen von Validierungen für Updates zu einer Entitätsklasse  
 Neben der Überprüfung von Werten während Änderungen können Sie auch Daten auf Gültigkeit prüfen, wenn versucht wird, eine vollständige Entitätsklasse zu aktualisieren. Validierung während eines versuchten Updates ermöglicht Ihnen, Werte in mehreren Spalten zu vergleichen, wenn die Geschäftsregeln dies erfordern. Das folgende Verfahren veranschaulicht die Validierung beim Versuch, eine vollständige Entitätsklasse zu aktualisieren.  
  
> [!NOTE]
>  Der Validierungscode für Updates vollständiger Entitätsklassen wird in der partiellen <xref:System.Data.Linq.DataContext>-Klasse ausgeführt (statt in der partiellen Klasse einer bestimmten Entitätsklasse).  
  
#### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>So validieren Sie Daten während eines Updates einer Entitätsklasse  
  
1. Öffnen oder erstellen Sie eine neue LINQ to SQL-Klassendatei (**dbml** Datei) in der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Doppelklicken Sie im **Projektmappen-Explorer** auf die **DBML**-Datei.)  
  
2. Mit der rechten Maustaste auf den O/R-Designer eines leeren Bereichs, und klicken Sie auf **Ansichtscode**.  
  
    Der Code-Editor wird mit einer partiellen Klasse für den `DataContext` geöffnet.  
  
3. Platzieren Sie den Cursor in die partielle Klasse für den `DataContext`.  
  
4. Für Visual Basic-Projekte:  
  
   1. Erweitern Sie die Liste **Methodenname**.  
  
   2. Klicken Sie auf **Update**_ENTITÄTSKLASSENNAME_.  
  
   3. Ein `Update` *ENTITÄTSKLASSENNAME* Methode wird der partiellen Klasse hinzugefügt.  
  
   4. Greifen Sie auf die Werte einzelner Spalten mithilfe des `instance`-Arguments zu, wie im folgenden Code dargestellt:  
  
      ```vb  
      If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then  
          Dim ErrorMessage As String = "Invalid data!"  
          Throw New Exception(ErrorMessage)  
      End If  
      ```  
  
      Für C#-Projekte:  
  
   5. Da C#-Projekte die Ereignishandler nicht automatisch generieren, können Sie IntelliSense verwenden, um die partielle erstellen `Update` *CLASSNAME* Methode.  
  
   6. Geben Sie `partial` und dann ein Leerzeichen ein, um auf die Liste der verfügbaren partiellen Methoden zuzugreifen. Klicken Sie auf die Updatemethode für die Klasse, der Sie Validierung hinzufügen möchten. Der folgende Code ähnelt dem Code, der generiert wird, bei der Auswahl einer `Update` *CLASSNAME* partielle Methode:  
  
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
 [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Überprüfen von Daten](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)
