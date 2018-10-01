---
title: Problembehandlung bei fehlerhaften Verweisen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual C# projects, references
- Visual Basic projects, references
- troubleshooting references
- referencing files from projects
- referencing components, troubleshooting
ms.assetid: 00a9ade9-652e-40de-8ada-85f63cd183ee
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6cee6fcd845630b7f980fab602193f845aab458c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514326"
---
# <a name="troubleshooting-broken-references"></a>Troubleshooting Broken References
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Problembehandlung bei fehlerhaften verweisen](https://docs.microsoft.com/visualstudio/ide/troubleshooting-broken-references).  
  
Wenn die Anwendung versucht, einen fehlerhaften Verweis zu verwenden, wird ein Ausnahmefehler generiert. Der Fehler wird in erster Linie dadurch ausgelöst, dass die Komponente, auf die verwiesen wird, nicht gefunden wurde. In anderen Fällen kann jedoch davon ausgegangen werden, dass der Verweis fehlerhaft ist. Diese Fälle werden im Folgenden aufgeführt:  
  
-   Der Verweispfad des Projekts ist falsch oder unvollständig.  
  
-   Die Datei, auf die verwiesen wird, wurde gelöscht.  
  
-   Die Datei, auf die verwiesen wird, wurde umbenannt.  
  
-   Das Herstellen der Netzwerkverbindung oder die Authentifizierung ist fehlgeschlagen.  
  
-   Der Verweis bezieht sich auf eine COM-Komponente, die auf dem Computer nicht installiert ist.  
  
 Im Folgenden werden Möglichkeiten zur Behebung dieser Probleme beschrieben.  
  
> [!NOTE]
>  Auf Dateien in Assemblys wird mit absoluten Pfaden in der Projektdatei verwiesen. Deshalb können Benutzer in einer Umgebung mit mehreren Entwicklern eine Assembly, für die ein Verweis vorhanden ist, in ihrer lokalen Umgebung möglicherweise nicht finden. Um diese Fehler zu vermeiden, empfiehlt es sich, in diesen Fällen Verweise zwischen Projekten hinzuzufügen. Weitere Informationen finden Sie unter [NIB How to: Add or Remove References By Using the Add Reference Dialog Box (Vorgehensweise: Hinzufügen und Entfernen von Verweisen mithilfe des Dialogfelds „Verweis hinzufügen“)](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) und [Programming with Assemblies (Programmieren mit Assemblys)](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6).  
  
## <a name="reference-path-is-incorrect"></a>Verweispfad ist falsch  
 Wenn von verschiedenen Computern aus auf Projekte zugegriffen wird, werden einige Verweise möglicherweise nicht gefunden, wenn sich eine Komponente auf den einzelnen Computern in unterschiedlichen Verzeichnissen befindet. Verweise werden unter dem Namen der Komponentendatei gespeichert (z.B. MeineKomponente). Wenn ein Verweis zu einem Projekt hinzugefügt wird, wird der Speicherort des Ordners der Komponentendatei (z.B. C:\MeineKomponenten\\) an die **Verweispfad**-Eigenschaft des Projekts angefügt.  
  
 Beim Öffnen versucht das Projekt, diese Komponentendateien in den Verzeichnissen im Verweispfad zu finden. Wenn das Projekt auf einem Computer geöffnet wird, auf dem die Komponente in einem anderen Verzeichnis gespeichert ist (z.B. D:\MeineKomponenten\\), kann der Verweis nicht gefunden werden, und in der Aufgabenliste wird ein Fehler angezeigt.  
  
 Sie können dieses Problem beheben, indem Sie den fehlerhaften Verweis löschen und ihn dann mithilfe des Dialogfelds „Verweis hinzufügen“ ersetzen. Alternativ können Sie auch den **Verweispfad**-Artikel in den Eigenschaftenseiten des Projekts verwenden und die Ordner in der Liste so ändern, dass sie auf die korrekten Speicherorte verweisen. Die **Verweispfad**-Eigenschaft wird für jeden Benutzer auf jedem Computer beibehalten. Deshalb hat eine Änderung Ihres Verweispfads keine Auswirkungen für andere Benutzer des Projekts.  
  
> [!TIP]
>  Bei Verweisen zwischen Projekten treten diese Probleme nicht auf. Verwenden Sie daher nach Möglichkeit Verweise zwischen Projekten anstatt Dateiverweise.  
  
#### <a name="to-fix-a-broken-project-reference-by-correcting-the-reference-path"></a>So reparieren Sie einen fehlerhaften Projektverweis durch Korrigieren des Verweispfads  
  
1.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Der **Projekt-Designer** wird angezeigt.  
  
3.  Wenn Sie Visual Basic verwenden, wählen Sie die Seite **Verweise** aus, und klicken Sie auf die Schaltfläche **Verweispfade**. Geben Sie im Dialogfeld **Verweispfade** im Feld **Ordner** den Pfad des Ordners mit dem Element an, auf das verwiesen werden soll, und klicken Sie dann auf die Schaltfläche **Ordner hinzufügen**.  
  
     - oder -   
  
     Wenn Sie Visual C# verwenden, wählen Sie die Seite **Verweispfade** aus. Geben Sie im Feld **Ordner** den Pfad des Ordners mit dem Element an, auf das verwiesen werden soll, und klicken Sie dann auf die Schaltfläche **Ordner hinzufügen**.  
  
## <a name="referenced-file-has-been-deleted"></a>Verweisdatei wurde gelöscht  
 Die Datei, auf die verwiesen wird, wurde möglicherweise gelöscht und ist nicht mehr auf dem Laufwerk vorhanden.  
  
#### <a name="to-fix-a-broken-project-reference-for-a-file-that-no-longer-exists-on-your-drive"></a>So reparieren Sie einen fehlerhaften Projektverweis auf eine Datei, die vom Laufwerk gelöscht wurde  
  
-   Löschen Sie den Verweis.  
  
-   Wenn der Verweis auf dem Computer an einem anderen Speicherort vorhanden ist, lesen Sie ihn von diesem Speicherort.  
  
-   Weitere Informationen finden Sie unter [NIB How to: Add or Remove References By Using the Add Reference Dialog Box (Vorgehensweise: Hinzufügen und Entfernen von Verweisen mithilfe des Dialogfelds „Verweis hinzufügen“)](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## <a name="referenced-file-has-been-renamed"></a>Verweisdatei wurde umbenannt  
 Die Datei, auf die verwiesen wird, wurde möglicherweise umbenannt.  
  
#### <a name="to-fix-a-broken-reference-for-a-file-that-has-been-renamed"></a>So korrigieren Sie einen fehlerhaften Verweis auf eine Datei, die umbenannt wurde  
  
-   Löschen Sie den Verweis, und fügen Sie dann einen Verweis auf die umbenannte Datei hinzu.  
  
-   Wenn der Verweis auf dem Computer an einem anderen Speicherort vorhanden ist, müssen Sie ihn von diesem Speicherort einlesen. Weitere Informationen finden Sie unter [NIB How to: Add or Remove References By Using the Add Reference Dialog Box (Vorgehensweise: Hinzufügen und Entfernen von Verweisen mithilfe des Dialogfelds „Verweis hinzufügen“)](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## <a name="network-connection-or-authentication-has-failed"></a>Fehler beim Herstellen der Netzwerkverbindung oder der Authentifizierung  
 Es kann viele mögliche Ursachen geben, warum auf Dateien nicht zugegriffen werden kann, z.B. eine fehlerhafte Netzwerkverbindung oder eine fehlgeschlagene Authentifizierung. Für jede dieser Ursachen kann es eine bestimmte Maßnahme zur Fehlerbehebung geben. Für den Zugriff auf die benötigten Ressourcen müssen Sie sich z.B. möglicherweise an den lokalen Administrator wenden. Es ist jedoch immer möglich, den Verweis zu löschen und den Code, in dem er verwendet wurde, entsprechend zu ändern. Weitere Informationen finden Sie unter [NIB How to: Add or Remove References By Using the Add Reference Dialog Box (Vorgehensweise: Hinzufügen und Entfernen von Verweisen mithilfe des Dialogfelds „Verweis hinzufügen“)](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## <a name="com-component-is-not-installed-on-computer"></a>COM-Komponente nicht auf Computer installiert  
 Wenn ein Benutzer einen Verweis auf eine COM-Komponente hinzugefügt hat und ein anderer Benutzer nun versucht, den Code auf einem Computer auszuführen, auf dem diese Komponente nicht installiert ist, erhält er die Fehlermeldung, dass der Verweis fehlerhaft ist. Der Fehler wird behoben, indem die Komponente auf dem zweiten Computer installiert wird. Weitere Informationen über das Verwenden von Verweisen auf COM-Komponenten in Projekten finden Sie unter [COM Interoperability in .NET Framework Applications (COM-Interoperabilität in .NET Framework-Anwendungen)](http://msdn.microsoft.com/library/f5a72143-c268-4dff-a019-974ad940e17d).  
  
## <a name="see-also"></a>Siehe auch  
 [Introduction to the Project Designer (Einführung in den Projekt-Designer)](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)   
 [Seite „Verweise“, Projekt-Designer (Visual Basic)](../ide/reference/references-page-project-designer-visual-basic.md)   
 [NIB How to: Add or Remove References By Using the Add Reference Dialog Box (Vorgehensweise: Hinzufügen und Entfernen von Verweisen mithilfe des Dialogfelds „Verweis hinzufügen“)](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)



