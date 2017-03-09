---
title: "Vorgehensweise: Hinzuf&#252;gen von Validierungen zu Entit&#228;tsklassen | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Vorgehensweise: Hinzuf&#252;gen von Validierungen zu Entit&#228;tsklassen
Durch den Vorgang der *Validierung* von Entitätsklassen wird bestätigt, dass die in Datenobjekte eingegebenen Werte den Einschränkungen eines Objektschemas oder den bestehenden Regeln für die Anwendung entsprechen.Es dient der Fehlervermeidung, Daten vor dem Senden von Updates an zugrunde liegende Datenbanken auf Gültigkeit zu überprüfen.Dadurch wird auch die potenzielle Anzahl von Roundtrips zwischen einer Anwendung und der Datenbank verringert.  
  
 Der [Object Relational Designer \(O\/R\-Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md) stellt partielle Methoden bereit, mit denen der Benutzer den durch den Designer generierten Code erweitern kann, der beim Einfügen, Aktualisieren und Löschen ganzer Entitäten oder während bzw. nach dem Ändern einzelner Spalten ausgeführt wird.  
  
> [!NOTE]
>  Dieses Thema beschreibt die grundlegenden Schritte zum Hinzufügen von Validierungen zu Entitätsklassen mit dem [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Da es schwierig sein könnte, diese generischen Schritte ohne Verweis auf eine bestimmte Entitätsklasse nachzuvollziehen, wird eine exemplarische Vorgehensweise mit tatsächlichen Daten zur Verfügung gestellt.Weitere schrittweise Anleitungen zur Konfiguration der Validierung mit dem [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] finden Sie unter [Exemplarische Vorgehensweise: Hinzufügen von Validierung zu Entitätsklassen](../Topic/Walkthrough:%20Adding%20Validation%20to%20Entity%20Classes.md).  
  
## Hinzufügen von Validierungen bei Werteänderungen in einer bestimmten Spalte  
 Dieses Verfahren veranschaulicht, wie Daten auf Gültigkeit geprüft werden, wenn sich der Wert in einer Spalte ändert.Da die Validierung innerhalb der Klassendefinition \(nicht der Benutzeroberfläche\) ausgeführt wird, wird eine Ausnahme ausgelöst, wenn die Validierung aufgrund des Werts fehlschlägt.Implementieren Sie eine Fehlerbehandlung für den Code in der Anwendung, der die Änderung von Spaltenwerten durchführt.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### So validieren Sie Daten während einer Änderung eines Spaltenwerts  
  
1.  Erstellen Sie eine neue LINQ to SQL\-Klassendatei \(**.dbml**\-Datei\) im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], oder öffnen Sie eine vorhandene Datei.\(Doppelklicken Sie im **Projektmappen\-Explorer** auf die **.dbml**\-Datei.\)  
  
2.  Klicken Sie im O\/R\-Designer mit der rechten Maustaste auf die Klasse, der Sie Validierungen hinzufügen möchten, und klicken Sie dann auf **Code anzeigen**.  
  
     Der Code\-Editor wird mit einer partiellen Klasse für die ausgewählte Entitätsklasse geöffnet.  
  
3.  Platzieren Sie den Cursor in der partiellen Klasse.  
  
4.  Für Visual Basic\-Projekte:  
  
    1.  Erweitern Sie die Liste **Methodenname**.  
  
    2.  Suchen Sie die **On***COLUMNNAME***Changing**\-Methode für die Spalte, der Sie Validierung hinzufügen möchten.  
  
    3.  Der partiellen Klasse wird eine `On`*COLUMNNAME*`Changing`\-Methode hinzugefügt.  
  
    4.  Fügen Sie den folgenden Code hinzu, um zunächst zu überprüfen, ob ein Wert eingegeben wurde, und dann sicherzustellen, dass der für die Spalte eingegebene Wert für die Anwendung gültig ist.Das `value`\-Argument enthält den vorgeschlagenen Wert, fügen Sie daher Logik hinzu, um sicherzustellen, das es sich um einen gültigen Wert handelt:  
  
        ```vb#  
        If value.HasValue Then  
            ' Add code to ensure that the value is acceptable.  
            ' If value < 1 Then  
            '    Throw New Exception("Invalid data!")  
            ' End If  
        End If  
        ```  
  
     Für C\#\-Projekte:  
  
    1.  Da C\#\-Projekte die Ereignishandler nicht automatisch generieren, können Sie IntelliSense verwenden, um die partiellen Methoden für die Spaltenänderung zu erstellen.  
  
         Geben Sie `partial` und dann ein Leerzeichen ein, um auf die Liste der verfügbaren partiellen Methoden zuzugreifen.Klicken Sie auf die Methode zur Spaltenänderung für die Spalte, der Sie Validierung hinzufügen möchten.Der folgende Code ähnelt dem Code, der generiert wird, wenn Sie eine partielle Methode zur Spaltenänderung auswählen:  
  
        ```c#  
        partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)  
            {  
               throw new System.NotImplementedException();  
            }  
  
        ```  
  
## Hinzufügen von Validierungen für Updates zu einer Entitätsklasse  
 Neben der Überprüfung von Werten während Änderungen können Sie auch Daten auf Gültigkeit prüfen, wenn versucht wird, eine vollständige Entitätsklasse zu aktualisieren.Validierung während eines versuchten Updates ermöglicht Ihnen, Werte in mehreren Spalten zu vergleichen, wenn die Geschäftsregeln dies erfordern.Das folgende Verfahren veranschaulicht die Validierung beim Versuch, eine vollständige Entitätsklasse zu aktualisieren.  
  
> [!NOTE]
>  Der Validierungscode für Updates vollständiger Entitätsklassen wird in der partiellen <xref:System.Data.Linq.DataContext>\-Klasse ausgeführt \(statt in der partiellen Klasse einer bestimmten Entitätsklasse\).  
  
#### So validieren Sie Daten während des Updates einer Entitätsklasse  
  
1.  Erstellen Sie eine neue LINQ to SQL\-Klassendatei \(**.dbml**\-Datei\) im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], oder öffnen Sie eine vorhandene Datei.\(Doppelklicken Sie im **Projektmappen\-Explorer** auf die **.dbml**\-Datei.\)  
  
2.  Klicken Sie im O\/R\-Designer mit der rechten Maustaste in einen leeren Bereich, und klicken Sie auf **Code anzeigen**.  
  
     Der Code\-Editor wird mit einer partiellen Klasse für den `DataContext` geöffnet.  
  
3.  Platzieren Sie den Cursor in die partielle Klasse für den `DataContext`.  
  
4.  Für Visual Basic\-Projekte:  
  
    1.  Erweitern Sie die Liste **Methodenname**.  
  
    2.  Klicken Sie auf **Aktualisieren***ENTITYCLASSNAME*.  
  
    3.  Der partiellen Klasse wird eine `Update`*ENTITYCLASSNAME*\-Methode hinzugefügt.  
  
    4.  Greifen Sie auf die Werte einzelner Spalten mithilfe des `instance`\-Arguments zu, wie im folgenden Code dargestellt:  
  
        ```vb#  
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then  
            Dim ErrorMessage As String = "Invalid data!"  
            Throw New Exception(ErrorMessage)  
        End If  
        ```  
  
     Für C\#\-Projekte:  
  
    1.  Da C\#\-Projekte die Ereignishandler nicht automatisch generieren, können Sie IntelliSense verwenden, um die partielle `Update`*CLASSNAME*\-Methode zu erstellen.  
  
    2.  Geben Sie `partial` und dann ein Leerzeichen ein, um auf die Liste der verfügbaren partiellen Methoden zuzugreifen.Klicken Sie auf die Updatemethode für die Klasse, der Sie Validierung hinzufügen möchten.Der folgende Code ähnelt dem Code, der generiert wird, wenn Sie eine partielle `Update`\-*CLASSNAME*Methode auswählen:  
  
        ```c#  
        partial void UpdateCLASSNAME(CLASSNAME instance)  
        {  
            if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))  
            {  
                string ErrorMessage = "Invalid data!";  
                throw new System.Exception(ErrorMessage);  
            }  
        }  
        ```  
  
## Siehe auch  
 [Object Relational Designer \(O\/R\-Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)