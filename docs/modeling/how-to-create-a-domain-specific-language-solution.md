---
title: "Gewusst wie: Erstellen einer domänenspezifischen Sprachlösung | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
ms.assetid: e585b63b-34d2-405a-8d81-39ea22317975
caps.latest.revision: 41
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: b7c6f6f854e17e9b3b19f277d49674c311edb41b
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Gewusst wie: Erstellen einer domänenspezifischen Sprachlösung
Erstellt eine domänenspezifische Sprache (DSL) mit einem speziellen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Lösung.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Bevor Sie dieses Verfahren starten können, müssen Sie zunächst diese Komponenten installieren:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.Microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.Microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|Visual Studio Visualization and Modeling SDK||  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
## <a name="creating-a-domain-specific-language-solution"></a>Erstellen einer domänenspezifischen Sprache-Lösung  
  
#### <a name="to-create-a-domain-specific-language-solution"></a>Zum Erstellen einer domänenspezifischen Sprache-Lösung  
  
1.  Starten Sie DSL-Assistenten.  
  
    1.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
    2.  Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
    3.  Klicken Sie unter **Projekttypen**, erweitern Sie die **andere Projekttypen** Knoten, und klicken Sie auf **Erweiterbarkeit**.  
  
    4.  Klicken Sie auf **domänenspezifischen Sprachdesigner**.  
  
    5.  In der **Namen** Geben Sie einen Namen für die Projektmappe. Klicken Sie auf **OK**.  
  
         Die **domänenspezifischen Sprachdesigner-Assistenten** wird angezeigt.  
  
        > [!NOTE]
        >  Vorzugsweise sollte der von Ihnen eingegebene Name ein gültiger C#-Bezeichner sein, da er möglicherweise zum Generieren von Code verwendet werden.  
  
     ![Erstellen von DSL-Dialogfeld](../modeling/media/create_dsldialog.png "Create_DSLDialog")  
  
2.  Wählen Sie eine DSL-Vorlage.  
  
     Auf der **Domain-Specific Language-Optionen auswählen** Seite, wählen Sie eine der Lösungsvorlagen wie z. B. **minimale Sprache**. Wählen Sie eine Vorlage, die die DSL ähnelt, die Sie erstellen möchten.  
  
     Weitere Informationen zu Vorlagen finden Sie unter [auswählen eine domänenspezifische Sprache Projektmappenvorlage](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
3.  Geben Sie die Erweiterung auf der **Dateierweiterung** Seite. Auf dem Computer eindeutig sein, und in jedem Computer, auf denen Sie die DSL installieren möchten. Daraufhin sollte die Meldung **keine Applikationen oder Visual Studio-Editoren mithilfe dieser Erweiterung**.  
  
    -   Wenn Sie die Erweiterung in vorherigen experimentelle DSLs verwendet haben, die nicht vollständig installiert wurden, können Sie löschen diese out mithilfe der **Zurücksetzen der experimentellen Instanz** -Tool, das im Zwischendateiverzeichnis der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] SDK im Menü.  
  
    -   Wenn ein anderer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Erweiterung, die diese Erweiterung verwendet vollständig auf Ihrem Computer installiert wurde, sollten Sie es deinstallieren. Auf der **Tools** Menü klicken Sie auf **Extension Manager**.  
  
4.  Überprüfen Sie und bei Bedarf passen Sie an, die Felder in den verbleibenden Seiten des Assistenten. Wenn Sie mit den Einstellungen zufrieden sind, klicken Sie auf **Fertig stellen**. Weitere Informationen zu den Optionen finden Sie unter [DSL-Designer Assistentenseiten](#settings).  
  
     Der Assistent erstellt eine Projektmappe mit zwei Projekten, die benannt werden **Dsl** und **DslPackage**.  
  
    > [!NOTE]
    >  Wenn Sie eine Nachricht, die Sie nicht benachrichtigt werden, zum Ausführen von Textvorlagen aus nicht vertrauenswürdigen Quellen auf **OK**. Sie können diese Meldung nicht in der Zukunft festlegen.  
  
##  <a name="a-namesettingsa-the-dsl-designer-wizard-pages"></a><a name="settings"></a>Die Seiten der DSL-Designer-Assistent  
 Sie können einige Felder, deren Standardwerte unverändert lassen. Stellen Sie jedoch sicher, dass Sie im Feld Erweiterung festlegen.  
  
### <a name="solution-settings-page"></a>Projektmappen-Einstellungsseite  
 **Welche Vorlage möchten Sie Ihre domänenspezifischen Sprache basieren?**  
 Wählen Sie eine Vorlage, die die DSL ähnelt, die Sie erstellen möchten. Die anderen Vorlagen bieten praktische Ausgangspunkte. Wenn Sie eine Projektmappenvorlage auswählen, zeigt der Assistent eine Beschreibung ein. Weitere Informationen zu Vorlagen finden Sie unter [auswählen eine domänenspezifische Sprache Projektmappenvorlage](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
 **Was möchten Sie Ihre einer domänenspezifischen Sprache zu nennen?**  
 Der Standardwert ist der Projektmappenname. Aus diesem Wert wird Code generiert. Es muss als C#-Klassenname gültig sein.  
  
### <a name="file-extension-page"></a>Seite "Erweiterung"  
 **Welche Erweiterung Modell sollten Dateien verwenden?**  
 Geben Sie eine neue Erweiterung.  
  
 Stellen Sie sicher, dass diese Erweiterung nicht bereits für die Verwendung auf diesem Computer wie folgt registriert wurde:  
  
 Suchen Sie unter **andere Tools und Applikationen, behandeln diese Erweiterung registriert**. Wenn die Meldung **keine Applikationen oder Visual Studio-Editoren mithilfe dieser Erweiterung**, können Sie diese Erweiterung verwenden.  
  
 Wenn Sie eine Liste der Tools oder Pakete angezeigt wird, sollten Sie eine der folgenden durchführen:  
  
-   Geben Sie eine andere Datei-Erweiterung.  
  
     \- oder –  
  
-   Zurücksetzen der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] experimentelle Instanz. Dies wird alle DSLs aufgehoben, die Sie zuvor erstellt haben. Auf der **starten** Menü klicken Sie auf **Programme**, **Microsoft Visual Studio 2010 SDK**, **Tools**, und klicken Sie dann **Zurücksetzen die Microsoft Visual Studio 2010 experimentellen Instanz**. Sie können eine beliebige andere DSLs neu erstellen, die Sie wiederverwenden möchten.  
  
     \- oder –  
  
-   Wenn eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Erweiterung, die diese Erweiterung verwendet vollständig auf Ihrem Computer installiert ist, deinstallieren Sie es. Auf der **Tools** Menü klicken Sie auf **Extension Manager**.  
  
### <a name="product-settings-page"></a>Produkt-Einstellungsseite  
 **Was ist der Name des Produkts, das die neue domänenspezifische Sprache gehört?**  
 Der Standardwert ist der Name der DSL.  
  
 Dieser Wert wird in Windows Explorer (oder Datei-Explorer), um Dateien zu beschreiben, die haben diese Erweiterung, verwendet.  
  
 **Was ist der Name des Unternehmens, das das Produkt gehört?**  
 Der Unternehmensname Ihres.  
  
 Dieser Wert wird in der AssemblyInfo-Eigenschaften des DSL-Paket integriert.  
  
 **Was ist der Stammnamespace für Projekte in dieser Lösung?**  
 Der Standardwert ist ein Name, der von Ihrem Unternehmen besteht und Produktnamen.  
  
### <a name="signing-page"></a>Seite "Signierung"  
 **Erstellen Sie eine Schlüsseldatei mit starkem Namen**  
 Die Standardoption ist, um einen neuen Schlüssel zum Signieren Ihrer DSL-Assembly zu erstellen.  
  
 **Verwenden Sie die vorhandenen Schlüssel mit starkem Namen**  
 Verwenden Sie diese Option, wenn Sie Ihre DSL in einer anderen Assembly integrieren möchten.  
  
 Weitere Informationen über starke Namen finden Sie unter [erstellen und Assemblys mit starkem Namen](http://go.microsoft.com/fwlink/?LinkId=186073).  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: definieren eine domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md)   
 [Tools für domänenspezifische Sprache – Glossar](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)

