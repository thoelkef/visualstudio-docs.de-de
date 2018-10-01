---
title: 'Vorgehensweise: Suchen und Organisieren von Projekt- und Elementvorlagen | Microsoft-Dokumentation'
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
- project templates [Visual Studio], locations
- custom template locations [Visual Studio]
- item templates, locations
- Visual Studio templates, locations
- project templates [Visual Studio], displaying
- templates [Visual Studio], locations
ms.assetid: 71f9ed52-c9c9-4818-9bce-c279ffaa0438
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 08817b551d015481000d3151fb054ee5803ee6f8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511370"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Gewusst wie: Suchen und Organisieren von Projekt- und Elementvorlagen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [wie: Suchen und Organisieren von Projekt- und Elementvorlagen](https://docs.microsoft.com/visualstudio/ide/how-to-locate-and-organize-project-and-item-templates).  
  
Vorlagendateien müssen an einem Speicherort abgelegt werden, an dem Visual Studio nach den Vorlagen sucht, damit sie im Dialogfeld **Neues Projekt** und **Neues Element hinzufügen** angezeigt werden können. Sie können benutzerdefinierte Unterkategorien für Vorlagen erstellen, damit die Unterkategorien auch auf der Benutzeroberfläche angezeigt werden.  
  
## <a name="locating-templates"></a>Suchen nach Vorlagen  
 Visual Studio sucht standardmäßig an zwei Orten nach Projekt- und Elementvorlagen. Wenn eine komprimierte Datei, die eine VSTEMPLATE-Datei enthält, an einem dieser Speicherorte vorhanden ist, wird in den Dialogfeldern **Neues Projekt** bzw. **Neues Element hinzufügen** eine Vorlage angezeigt.  
  
### <a name="installed-templates"></a>Installierte Vorlagen  
 Mit dem Produkt installierte Vorlagen befinden sich standardmäßig in folgenden Verzeichnissen:  
  
-   \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\\*Language*\\*Locale*\  
  
-   \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\\*Language*\\*Locale\\*  
  
 Das folgende Verzeichnis enthält beispielsweise die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projektvorlagen für Englisch:  
  
 C:\\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\VisualBasic\1033\  
  
### <a name="custom-templates"></a>Benutzerdefinierte Vorlagen  
 Benutzerdefinierte Vorlagen befinden sich standardmäßig in folgenden Verzeichnissen:  
  
-   \Eigene Dateien\Visual Studio *Version*Templates\ProjectTemplates\\*Language*\  
  
-   \Eigene Dateien\Visual Studio *Version*\Templates\ItemTemplates\\*Language*\  
  
 Im folgenden Verzeichnis sind beispielsweise benutzerdefinierte [!INCLUDE[csprcs](../includes/csprcs-md.md)]-Projektvorlagen enthalten:  
  
 C:\Documents und Einstellungen\Benutzername\Eigene Dokumente\\< Visual Studio-Version\>\Templates\ProjectTemplates\Visual C# \  
  
 Benutzerdefinierte Vorlagen enthalten kein Unterverzeichnis für lokalisierte Vorlagen. Sie können das Standardverzeichnis für benutzerdefinierte Vorlagen im Dialogfeld **Optionen** unter **Umgebung\Projekte und Projektmappen** ändern.  
  
## <a name="organizing-templates"></a>Organisieren von Vorlagen  
 Die Kategorien in den Dialogfeldern **Neues Projekt** und **Neues Element hinzufügen** spiegeln die Verzeichnisstrukturen wider, so wie sie an den Speicherorten für installierte und benutzerdefinierte Vorlagen angelegt sind. Sie können diese Verzeichnisstrukturen ändern, um Ihre Vorlagen in einer sinnvollen Weise zu organisieren.  
  
> [!NOTE]
>  Auf Programmiersprachenebene können keine neuen Kategorien erstellt werden. Neue Kategorien können nur innerhalb der einzelnen Programmiersprachen erstellt werden.  
  
 Wenn die Verzeichnisstrukturen installierter und benutzerdefinierter Vorlagen einer bestimmten Programmiersprache nicht dieselbe Struktur aufweisen (ein Ordner verfügt beispielsweise über Unterverzeichnisse, die im anderen Ordner nicht enthalten sind), handelt es sich bei den Kategorien im Dialogfeld **Neues Projekt** um eine Zusammenfassung aller Kategorien.  
  
### <a name="organizing-installed-templates"></a>Organisieren von installierten Vorlagen  
 Sie können installierte Vorlagen organisieren, indem Sie Unterverzeichnisse innerhalb des Programmiersprachenordners erstellen. Diese Unterverzeichnisse werden innerhalb der einzelnen Programmiersprachen als virtuelle Ordner in den Dialogfeldern **Neues Projekt** und **Neues Element hinzufügen** angezeigt.  
  
##### <a name="to-create-new-installed-project-template-categories"></a>So erstellen Sie neue Kategorien für installierte Projektvorlagen  
  
1.  Erstellen Sie einen Ordner im Programmiersprachenordner des Verzeichnisses für die installierte Vorlage. Um z. B. die Kategorie Office für [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projektvorlagen einzurichten, würden Sie das folgende Verzeichnis erstellen:  
  
     \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\VisualBasic\1033\Office\  
  
2.  Fügen Sie alle Vorlagen für diese Kategorie in den neuen Ordner ein.  
  
3.  Schließen Sie alle Instanzen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4.  Klicken Sie im Menü **Start** auf **Ausführen**, geben Sie **cmd** ein, und klicken Sie auf **OK**.  
  
5.  Suchen Sie an der Eingabeaufforderung das Verzeichnis, das „devenv.exe“ enthält, und geben Sie **devenv /installvstemplates** ein.  
  
6.  Führen Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aus.  
  
7.  Klicken Sie im Menü **Datei** auf **Neu** und dann auf **Projekt**.  
  
8.  Stellen Sie sicher, dass die Kategorie „Office“ im Dialogfeld **Neues Projekt** im Bereich **Projekttypen** unter [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] angezeigt wird.  
  
 Sie können auch eine Teilmenge von Projektelementvorlagen in einem benutzerdefinierten Ordner gruppieren.  
  
##### <a name="to-create-new-installed-item-template-categories"></a>So erstellen Sie neue Kategorien für installierte Elementvorlagen  
  
1.  Erstellen Sie einen Ordner im Programmiersprachenordner des Verzeichnisses für die installierte Vorlage. Um z. B. die Kategorie Web für [!INCLUDE[csprcs](../includes/csprcs-md.md)] -Elementvorlagen einzurichten, würden Sie das folgende Verzeichnis erstellen:  
  
     \\*\VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\CSharp\1033\Web\  
  
2.  Fügen Sie alle Vorlagen für diese Kategorie in den neuen Ordner ein.  
  
3.  Schließen Sie alle Instanzen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4.  Klicken Sie im Menü **Start** auf **Ausführen**, geben Sie **cmd** ein, und klicken Sie auf **OK**.  
  
5.  Suchen Sie an der Eingabeaufforderung das Verzeichnis, das „devenv.exe“ enthält, und geben Sie **devenv /setup** ein.  
  
6.  Führen Sie aus [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
7.  Erstellen Sie ein Projekt, oder öffnen Sie ein vorhandenes Projekt.  
  
8.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
9. Stellen Sie sicher, dass die Kategorie „Web“ im Dialogfeld **Neues Element hinzufügen** im Bereich **Projekttypen** angezeigt wird.  
  
### <a name="organizing-custom-templates"></a>Organisieren von benutzerdefinierten Vorlagen  
 Benutzerdefinierte Vorlagen können in eigenen Kategorien organisiert werden, indem dem Speicherort für benutzerdefinierte Vorlagen neue Ordner hinzugefügt werden. Im Dialogfeld **Neues Projekt** werden alle Änderungen angezeigt, die Sie an den Vorlagenkategorien vornehmen.  
  
##### <a name="to-create-new-custom-project-template-categories"></a>So erstellen Sie neue Kategorien für benutzerdefinierte Projektvorlagen  
  
1.  Erstellen Sie im Verzeichnis für benutzerdefinierte Projektvorlagen einen Ordner im jeweiligen Programmiersprachenordner. Um z. B. die Kategorie "HelloWorld" für [!INCLUDE[csprcs](../includes/csprcs-md.md)] -Vorlagen einzurichten, erstellen Sie das folgende Verzeichnis:  
  
     \My Dokumente\\< Visual Studio-Version\>\Templates\ProjectTemplates\CSharp\HelloWorld\  
  
2.  Fügen Sie alle Vorlagen für diese Kategorie in den neuen Ordner ein.  
  
3.  Klicken Sie im Menü **Datei** auf **Neu**und dann auf **Projekt**.  
  
4.  Stellen Sie sicher, dass die Kategorie „HelloWorld“ im Dialogfeld **Neues Projekt** im Bereich **Projekttypen** unter [!INCLUDE[csprcs](../includes/csprcs-md.md)] angezeigt wird.  
  
 Sie können auch eine Teilmenge von benutzerdefinierten Elementvorlagen in einem benutzerdefinierten Ordner gruppieren.  
  
##### <a name="to-create-new-custom-item-template-categories"></a>So erstellen Sie neue Kategorien für benutzerdefinierte Elementvorlagen  
  
1.  Erstellen Sie im Verzeichnis für benutzerdefinierte Elementvorlagen einen Ordner im jeweiligen Programmiersprachenordner. Um z. B. die Kategorie HelloWorld für [!INCLUDE[csprcs](../includes/csprcs-md.md)] -Vorlagen einzurichten, würden Sie das folgende Verzeichnis erstellen:  
  
     \My Dokumente\\< Visual Studio-Version\>\Templates\ItemTemplates\CSharp\HelloWorld\  
  
2.  Fügen Sie alle Vorlagen für diese Kategorie in den neuen Ordner ein.  
  
3.  Erstellen Sie ein Projekt, oder öffnen Sie ein vorhandenes Projekt.  
  
4.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
5.  Stellen Sie sicher, dass die Kategorie „HelloWorld“ im Dialogfeld **Neues Element hinzufügen** im Bereich **Projekttypen** angezeigt wird.  
  
### <a name="displaying-templates-in-parent-categories"></a>Anzeigen von Vorlagen in übergeordneten Kategorien  
 Sie können in Unterkategorien enthaltene Vorlagen in den übergeordneten Kategorien anzeigen lassen, indem Sie das `NumberOfParentCategoriesToRollUp`-Element in der VSTEMPLATE-Datei verwenden. Diese Schritte sind für Projektvorlagen und Elementvorlagen identisch.  
  
##### <a name="to-display-templates-in-parent-categories"></a>So zeigen Sie Vorlagen in übergeordneten Kategorien an  
  
1.  Suchen Sie die ZIP-Datei, die die Vorlage enthält.  
  
2.  Extrahieren Sie die ZIP-Datei.  
  
3.  Öffnen Sie die VSTEMPLATE-Datei in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4.  Fügen Sie im `TemplateData`-Element ein `NumberOfParentCategoriesToRollUp`-Element hinzu. Durch den folgenden Code wird die Vorlage beispielsweise in der unmittelbar übergeordneten Kategorie, nicht jedoch in höheren Kategorien angezeigt.  
  
    ```  
    <TemplateData>  
        ...  
        <NumberOfParentCategoriesToRollUp>  
            1  
        </NumberOfParentCategoriesToRollUp>  
        ...  
    </TemplateData>  
    ```  
  
5.  Speichern und schließen Sie die VSTEMPLATE-Datei.  
  
6.  Wählen Sie die Dateien in der Vorlage aus, klicken Sie mit der rechten Maustaste auf die Auswahl, klicken Sie auf **Senden an**, und klicken Sie dann auf **ZIP-komprimierten Ordner**. Die Dateien werden in eine ZIP-Datei komprimiert.  
  
7.  Löschen Sie die extrahierten Vorlagendateien und die alte ZIP-Datei der Vorlage.  
  
8.  Fügen Sie die neue ZIP-Datei in das Verzeichnis ein, in dem sich die gelöschte ZIP-Datei befunden hat.  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen von Vorlagen](../ide/customizing-project-and-item-templates.md)   
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [NumberOfParentCategoriesToRollUp (Visual Studio-Vorlagen)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)   
 [Vorgehensweise: Erstellen von Projektvorlagen](../ide/how-to-create-project-templates.md)   
 [Gewusst wie: Erstellen von Elementvorlagen](../ide/how-to-create-item-templates.md)



