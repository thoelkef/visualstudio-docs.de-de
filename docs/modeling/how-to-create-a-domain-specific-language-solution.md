---
title: "Vorgehensweise: Erstellen Sie eine Projektmappe einer domänenspezifischen Sprache | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8a8b349e43f4728fee3ec676a689e6ba03cde758
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Gewusst wie: Erstellen einer domänenspezifischen Sprachlösung
Eine domänenspezifische Sprache (DSL) wird mithilfe eines speziellen erstellt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Lösung.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Bevor Sie dieses Verfahren starten können, müssen Sie zunächst diese Komponenten installieren:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|Visual Studio Visualization and Modeling SDK||  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
## <a name="creating-a-domain-specific-language-solution"></a>Erstellen einer Projektmappe einer domänenspezifischen Sprache  
  
#### <a name="to-create-a-domain-specific-language-solution"></a>So erstellen Sie eine Projektmappe einer domänenspezifischen Sprache  
  
1.  Starten Sie DSL-Assistenten.  
  
    1.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
    2.  Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
    3.  Klicken Sie unter **-Projekttypen**, erweitern Sie die **andere Projekttypen** Knoten, und klicken Sie auf **Erweiterbarkeit**.  
  
    4.  Klicken Sie auf **einer domänenspezifischen Sprachdesigner**.  
  
    5.  In der **Namen** geben einen Namen für die Projektmappe. Klicken Sie auf **OK**.  
  
         Die **einer domänenspezifischen Sprache-Designer-Assistenten** angezeigt wird.  
  
        > [!NOTE]
        >  Vorzugsweise sollte der von Ihnen eingegebene Name ein gültiger Visual C#-Bezeichner sein, da es möglicherweise zur Generierung von Code verwendet werden.  
  
     ![DSL-Dialogfeld "erstellen"](../modeling/media/create_dsldialog.png "Create_DSLDialog")  
  
2.  Wählen Sie eine DSL-Vorlage aus.  
  
     Auf der **einer domänenspezifischen Sprachoptionen auswählen** Seite, wählen Sie eine der Projektmappenvorlagen z. B. **minimale Sprache**. Wählen Sie eine Vorlage, die die DSL ähnelt, die Sie erstellen möchten.  
  
     Weitere Informationen zu Projektmappenvorlagen finden Sie unter [Auswählen einer domänenspezifischen Sprache Projektmappenvorlage](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
3.  Geben Sie eine Erweiterung auf die **Dateierweiterung** Seite. Auf dem Computer eindeutig sein und in jeder Computer, auf denen der DSL installiert werden soll. Daraufhin sollte die Meldung **keine Anwendungen oder Visual Studio-Editoren mithilfe dieser Erweiterung**.  
  
    -   Wenn Sie die Dateinamenerweiterung in vorherigen experimentellen konzentriert verwendet haben, die nicht vollständig installiert wurde, Sie können Löschen von deren Inhalten out mithilfe der **Zurücksetzen der experimentellen Instanz** Tool, das sich in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] SDK-Menü.  
  
    -   Wenn ein anderer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] diese Dateierweiterung Übermittlungserweiterungen vollständig auf Ihrem Computer installiert wurde, sollten Sie es deinstallieren. Auf der **Tools** Menü klicken Sie auf **Erweiterungs-Manager**.  
  
4.  Überprüfen Sie und bei Bedarf passen Sie an, die Felder in den verbleibenden Seiten des Assistenten. Wenn Sie mit den Einstellungen zufrieden sind, klicken Sie auf **Fertig stellen**. Weitere Informationen zu den Einstellungen finden Sie unter [DSL-Designer-Assistentenseiten](#settings).  
  
     Der Assistent erstellt eine Lösung, die zwei Projekte verfügt, das heißen **Dsl** und **DslPackage**.  
  
    > [!NOTE]
    >  Wenn Sie eine Meldung, die Sie nicht benachrichtigt werden sehen, klicken Sie zum Ausführen von Textvorlagen aus nicht vertrauenswürdigen Quellen **OK**. Legen Sie diese Meldung nicht mehr angezeigt.  
  
##  <a name="settings"></a>Die Seiten der DSL-Designer-Assistent  
 Sie können einige Felder die Standardwerte unverändert lassen. Allerdings stellen Sie sicher, dass Sie die Datei Erweiterungsfeld festlegen.  
  
### <a name="solution-settings-page"></a>Seite "Einstellungen" Lösung  
 **Welche Vorlage möchten Sie Ihre domänenspezifischen Sprache basieren?**  
 Wählen Sie eine Vorlage, die die DSL ähnelt, die Sie erstellen möchten. Die anderen Vorlagen bieten praktische Ausgangspunkte. Wenn Sie eine Projektmappe (Vorlage) auswählen, zeigt der Assistent eine Beschreibung an. Weitere Informationen zu Projektmappenvorlagen finden Sie unter [Auswählen einer domänenspezifischen Sprache Projektmappenvorlage](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
 **Was möchten Sie Ihre domänenspezifische Sprache zu nennen?**  
 Der Standardwert ist der Projektmappenname. Dieser Wert wird Code generiert. Es muss als C#-Klassenname gültig sein.  
  
### <a name="file-extension-page"></a>Seite Dateierweiterung  
 **Welche Erweiterung zu modellieren, sollten Dateien verwenden?**  
 Geben Sie eine neue Dateierweiterung ein.  
  
 Stellen Sie sicher, dass die Dateierweiterung nicht bereits für die Verwendung auf diesem Computer wie folgt registriert wurde:  
  
 Suchen Sie unter **anderen Tools und Anwendungen, behandeln diese Erweiterung registriert**. Wenn die Meldung **keine Anwendungen oder Visual Studio-Editoren mithilfe dieser Erweiterung**, können Sie diese Erweiterung verwenden.  
  
 Wenn Sie eine Liste der Tools oder Pakete angezeigt wird, sollten Sie eine der folgenden Schritte ausführen:  
  
-   Geben Sie eine andere Erweiterung ein.  
  
     \- oder –  
  
-   Zurücksetzen der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] experimentellen Instanz. Dadurch wird die aller der konzentriert aufgehoben, die Sie zuvor erstellt haben. Auf der **starten** Menü klicken Sie auf **Programme**, **Microsoft Visual Studio 2010 SDK**, **Tools**, und klicken Sie dann **Zurücksetzen der Microsoft Visual Studio 2010 experimentelle Instanz**. Sie können eine beliebige andere konzentriert neu erstellen, die Sie erneut verwenden möchten.  
  
     \- oder –  
  
-   Wenn eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] diese Dateierweiterung Übermittlungserweiterungen vollständig auf Ihrem Computer installiert wurde, deinstallieren Sie es. Auf der **Tools** Menü klicken Sie auf **Erweiterungs-Manager**.  
  
### <a name="product-settings-page"></a>Produkt-Einstellungsseite  
 **Wie lautet der Name des Produkts, das die neue domänenspezifische Sprache zu gehört?**  
 Der Standardwert ist der Name der DSL.  
  
 Dieser Wert wird verwendet, in Windows Explorer (oder Datei-Explorer), um Dateien zu beschreiben, die diese Erweiterung haben.  
  
 **Wie lautet der Name des Unternehmens, das das Produkt gehört?**  
 Den Namen Ihres Unternehmens.  
  
 Dieser Wert wird in die Eigenschaften "AssemblyInfo" DSL-Paket integriert.  
  
 **Was ist der Stammnamespace für Projekte in dieser Lösung?**  
 Wird standardmäßig einen Namen, die von Ihrem Unternehmen besteht und aus Produktnamen besteht.  
  
### <a name="signing-page"></a>Seite "Signierung"  
 **Erstellen Sie eine Schlüsseldatei mit starkem Namen**  
 Option "Default" ist einen neuen Schlüssel zum Signieren der DSL-Assembly zu erstellen.  
  
 **Verwenden Sie die vorhandenen Schlüssel mit starkem Namen**  
 Verwenden Sie diese Option, wenn Sie der DSL mit einer anderen Assembly integrieren möchten.  
  
 Weitere Informationen über starke Namen finden Sie unter [erstellen und Verwenden von Assemblys](http://go.microsoft.com/fwlink/?LinkId=186073).  

## <a name="see-also"></a>Siehe auch

[So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)  
[Domänenspezifische Sprache Tools Glossar](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
