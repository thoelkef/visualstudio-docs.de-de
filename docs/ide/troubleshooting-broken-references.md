---
title: "Problembehandlung bei fehlerhaften Verweisen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Verweisen auf Komponenten, Problembehandlung"
  - "Verweisen auf Dateien aus Projekten"
  - "Problembehandlung bei Verweisen"
  - "Visual Basic-Projekte, Referenzen"
  - "Visual C#-Projekte, Referenzen"
ms.assetid: 00a9ade9-652e-40de-8ada-85f63cd183ee
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Problembehandlung bei fehlerhaften Verweisen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn die Anwendung versucht, einen fehlerhaften Verweis zu verwenden, wird ein Ausnahmefehler generiert.  Der Fehler wird in erster Linie dadurch ausgelöst, dass die Komponente, auf die sich der Verweis beziehen soll, nicht gefunden wurde. In anderen Situationen kann davon ausgegangen werden, dass der Verweis fehlerhaft ist.  Diese Fälle werden in der folgenden Liste aufgeführt:  
  
-   Der Verweispfad des Projekts ist nicht richtig oder unvollständig.  
  
-   Die Datei, auf die verwiesen wird, wurde gelöscht.  
  
-   Die Datei, auf die verwiesen wird, wurde umbenannt.  
  
-   Fehler beim Herstellen der Netzwerkverbindung oder der Authentifizierung.  
  
-   Der Verweis bezieht sich auf eine COM\-Komponente, die auf dem Computer nicht installiert ist.  
  
 Im Folgenden werden Möglichkeiten zur Problembehebung beschrieben.  
  
> [!NOTE]
>  Auf Dateien in Assemblys wird mit absoluten Pfaden in der Projektdatei verwiesen.  Aus diesem Grund können Benutzer in einer Umgebung mit mehreren Entwicklern u. U. in ihrer lokalen Umgebung eine Assembly nicht finden, für die ein Verweis vorhanden ist.  Um diese Fehler zu vermeiden, empfiehlt es sich, Verweise zwischen Projekten hinzuzufügen.  Weitere Informationen finden Sie unter [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) und unter [Programmieren mit Assemblys](../Topic/Programming%20with%20Assemblies.md).  
  
## Der Verweispfad ist nicht richtig  
 Wenn von verschiedenen Computern auf Projekte zugegriffen wird, werden einige Verweise u. U. nicht gefunden, wenn sich eine Komponente auf den einzelnen Computern in unterschiedlichen Verzeichnissen befindet.  Verweise werden unter dem Namen der Komponentendatei gespeichert \(z. B. MeineKomponente\).  Beim Hinzufügen eines Verweises zu einem Projekt wird die Ordnerposition der Komponentendatei \(z. B. C:\\MeineKomponenten\\\) an die **ReferencePath**\-Eigenschaft des Projekts angefügt.  
  
 Beim Öffnen versucht das Projekt, die entsprechenden Komponentendateien in den Verzeichnissen im Verweispfad zu finden.  Wird das Projekt auf einem Computer geöffnet, auf dem sich die Komponente in einem anderen Verzeichnis befindet \(z. B. **D:\\MeineKomponenten**\), so wird der Verweis nicht gefunden und ein Fehler in der Taskliste angezeigt.  
  
 Zum Beheben dieses Problems können Sie den fehlerhaften Verweis löschen und ihn anschließend im Dialogfeld "Verweis hinzufügen" ersetzen.  Sie können auch das Element **Verweispfad** auf den Eigenschaftenseiten des Projekts verwenden und die Ordner in der Liste so ändern, dass sie auf die korrekten Speicherorte verweisen.  Die **Verweispfad**\-Eigenschaftwird für jeden Benutzer auf jedem Computer beibehalten.  Die Änderung Ihres Verweispfads wirkt sich somit für andere Benutzer des Projekts nicht aus.  
  
> [!TIP]
>  Bei Verweisen zwischen Projekten tritt dieses Problem nicht auf.  Verwenden Sie daher nach Möglichkeit Verweise zwischen Projekten anstelle von Dateiverweisen.  
  
#### So reparieren Sie einen fehlerhaften Projektverweis durch Korrigieren des Verweispfades  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf den Projektknoten, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Der **Projekt\-Designer** wird angezeigt.  
  
3.  Wenn Sie Visual Basic verwenden, wählen Sie die Seite **Verweise** aus, und klicken Sie auf die Schaltfläche **Verweispfade**.  Geben Sie im Dialogfeld **Verweispfade** im Feld **Ordner** den Pfad des Ordners mit dem Element an, auf das verwiesen werden soll, und klicken Sie dann auf die Schaltfläche **Ordner hinzufügen**.  
  
     \- oder \-  
  
     Wenn Sie Visual C\# verwenden, wählen Sie die Seite **Verweispfade** aus.  Geben Sie im Feld **Ordner** den Pfad des Ordners mit dem Element an, auf das verwiesen werden soll, und klicken Sie dann auf die Schaltfläche **Ordner hinzufügen**.  
  
## Die Datei, auf die verwiesen wird, wurde gelöscht  
 Unter Umständen wurde die Datei, auf die verwiesen wird, vom Laufwerk gelöscht.  
  
#### So reparieren Sie einen fehlerhaften Projektverweis auf eine Datei, die vom Laufwerk gelöscht wurde  
  
-   Löschen Sie den Verweis.  
  
-   Wenn der Verweis auf dem Computer unter einem anderen Speicherort vorhanden ist, lesen Sie ihn von diesem Speicherort.  
  
-   Weitere Informationen finden Sie unter [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## Die Datei, auf die verwiesen wird, wurde umbenannt  
 Unter Umständen wurde die Datei, auf die verwiesen wird, umbenannt.  
  
#### So korrigieren Sie einen fehlerhaften Verweis auf eine Datei, die umbenannt wurde  
  
-   Löschen Sie den Verweis, und fügen Sie anschließend einen Verweis auf die umbenannte Datei hinzu.  
  
-   Wenn der Verweis auf dem Computer unter einem anderen Speicherort vorhanden ist, müssen Sie ihn von diesem Speicherort einlesen.  Weitere Informationen finden Sie unter [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## Fehler beim Herstellen der Netzwerkverbindung oder der Authentifizierung  
 Für nicht zugängliche Dateien kann es viele verschiedene Gründe geben, z. B. eine fehlerhafte Netzwerkverbindung oder eine fehlgeschlagene Authentifizierung.  Für jede dieser Ursachen kann es eine bestimmte Maßnahme zur Fehlerbehebung geben. Für den Zugriff auf die benötigten Ressourcen müssen Sie sich beispielweise an den zuständigen Systemadministrator wenden.  Es ist jedoch immer möglich, den Verweis zu löschen und den Code, in dem er verwendet wurde, entsprechend zu ändern.  Weitere Informationen finden Sie unter [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## Eine COM\-Komponente ist nicht auf dem Computer installiert  
 Wenn ein Benutzer einen Verweis auf eine COM\-Komponente hinzufügt und ein anderer Benutzer nun versucht, den Code auf einem Computer auszuführen, auf dem diese Komponente nicht installiert ist, erhält er die Fehlermeldung, dass der Verweis fehlerhaft ist.  Der Fehler wird behoben, indem die Komponente auf dem zweiten Computer installiert wird.  Weitere Informationen über das Verwenden von Verweisen auf COM\-Komponenten in Projekten finden Sie unter [COM Interoperability in .NET Framework Applications](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications).  
  
## Siehe auch  
 [Introduction to the Project Designer](http://msdn.microsoft.com/de-de/898dd854-c98d-430c-ba1b-a913ce3c73d7)   
 [Seite "Verweise", Projekt\-Designer \(Visual Basic\)](../ide/reference/references-page-project-designer-visual-basic.md)   
 [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)