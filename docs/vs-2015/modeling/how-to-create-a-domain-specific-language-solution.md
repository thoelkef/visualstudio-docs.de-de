---
title: 'Vorgehensweise: Erstellen Sie eine DSL-Projektmappe | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
ms.assetid: e585b63b-34d2-405a-8d81-39ea22317975
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 57c843b7c556ac409a63d5e6c01e2699da59958b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60099571"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Vorgehensweise: Erstellen einer domänenspezifischen Sprachlösung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine domänenspezifische Sprache (DSL) wird erstellt, indem Sie mithilfe einer speziellen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Lösung.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Bevor Sie dieses Verfahren starten können, müssen Sie zunächst diese Komponenten installieren:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|Visual Studio Visualization and Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581)|  
  
## <a name="creating-a-domain-specific-language-solution"></a>Erstellen einer Lösung einer domänenspezifischen Sprache  
  
#### <a name="to-create-a-domain-specific-language-solution"></a>Zum Erstellen einer Lösung einer domänenspezifischen Sprache  
  
1. Starten Sie die DSL-Assistenten.  
  
   1. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
   2. Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
   3. Klicken Sie unter **Projekttypen**, erweitern Sie die **andere Projekttypen** Knoten, und klicken Sie auf **Erweiterbarkeit**.  
  
   4. Klicken Sie auf **domänenspezifischen Sprachdesigner**.  
  
   5. In der **Namen** geben einen Namen für die Lösung. Klicken Sie auf **OK**.  
  
       Die **Domain-Specific Language-Designer-Assistenten** angezeigt wird.  
  
      > [!NOTE]
      >  Vorzugsweise sollten die von Ihnen eingegebene Name ein gültiger Visual C#-Bezeichner, sein, da möglicherweise zum Generieren von Code verwendet werden.  
  
      ![DSL-Dialogfeld "erstellen"](../modeling/media/create-dsldialog.png "Create_DSLDialog")  
  
2. Wählen Sie eine DSL-Vorlage.  
  
    Auf der **domänenspezifische Sprachoptionen auswählen** Seite, wählen Sie eine der Lösungsvorlagen wie z. B. **minimale Sprache**. Wählen Sie eine Vorlage, die die DSL ähnelt, die Sie erstellen möchten.  
  
    Weitere Informationen zu Vorlagen finden Sie unter [Auswählen einer Lösungsvorlage für Domain-Specific Language](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
3. Geben Sie eine Dateinamenerweiterung auf die **Dateierweiterung** Seite. Es muss auf dem Computer eindeutig sein und in jeder Computer, auf denen Sie die DSL installieren möchten. Daraufhin sollte die Nachricht **keine Anwendungen oder Visual Studio-Editoren mithilfe dieser Erweiterung**.  
  
   - Wenn Sie die Dateinamenerweiterung in vorherigen experimentelle DSLs verwendet haben, die nicht vollständig installiert wurden, Sie können sie sich durch Löschen mit der **Zurücksetzen der experimentellen Instanz** -Tool, das im befinden die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] SDK-Menü.  
  
   - Wenn ein anderer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Erweiterung, die diese Dateierweiterung wird vollständig auf Ihrem Computer installiert wurde, sollten Sie es deinstallieren. Auf der **Tools** Menü klicken Sie auf **Erweiterungs-Manager**.  
  
4. Überprüfen Sie und bei Bedarf passen Sie an, die Felder in den verbleibenden Seiten des Assistenten. Wenn Sie mit den Einstellungen zufrieden sind, klicken Sie auf **Fertig stellen**. Weitere Informationen zu den Einstellungen finden Sie unter [DSL-Designer-Assistentenseiten](#settings).  
  
    Der Assistent erstellt eine Projektmappe mit zwei Projekten, die benannt werden **Dsl** und **DslPackage**.  
  
   > [!NOTE]
   >  Wenn Sie eine Meldung, die Sie benachrichtigt werden, nicht zum Ausführen von Textvorlagen aus nicht vertrauenswürdigen Quellen auf **OK**. Sie können diese Meldung nicht wieder angezeigt werden, festlegen.  
  
## <a name="settings"></a> Die DSL-Designer-Assistent-Seiten  
 Sie können einige Felder die Standardwerte unverändert lassen. Allerdings stellen Sie sicher, dass Sie das Feld für die Erweiterung festlegen.  
  
### <a name="solution-settings-page"></a>Seite "Lösung-Einstellungen"  
 **Welcher Vorlage soll auf Ihrer domänenspezifischen Sprache basieren?**  
 Wählen Sie eine Vorlage, die die DSL ähnelt, die Sie erstellen möchten. Die anderen Vorlagen bieten praktische Ausgangspunkte. Wenn Sie eine Vorlage auswählen, zeigt der Assistent eine Beschreibung an. Weitere Informationen zu Vorlagen finden Sie unter [Auswählen einer Lösungsvorlage für Domain-Specific Language](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
 **Was möchten Sie zum Benennen Ihrer domänenspezifischen Sprache?**  
 Der Standardwert ist der Projektmappenname. Von diesem Wert wird Code generiert. Es muss als C#-Klassenname gültig sein.  
  
### <a name="file-extension-page"></a>Seite "Dateierweiterung"-Datei  
 **Welche Erweiterung sollen Modelldateien verwenden?**  
 Geben Sie eine neue Dateierweiterung ein.  
  
 Stellen Sie sicher, dass diese Erweiterung nicht bereits für die Verwendung in diesem Computer wie folgt registriert wurde:  
  
 Suchen Sie unter **anderen Tools und Anwendungen registriert werden, um diese Erweiterung behandeln**. Wenn die Meldung **keine Anwendungen oder Visual Studio-Editoren mithilfe dieser Erweiterung**, können Sie diese Erweiterung verwenden.  
  
 Wenn Sie eine Liste der Tools oder Pakete angezeigt wird, sollten Sie eine der folgenden tun:  
  
- Geben Sie eine andere Dateinamenerweiterung.  
  
     \- oder –  
  
- Zurücksetzen der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] experimentelle Instanz. Dadurch werden alle der DSLs Aufheben der Registrierung, die Sie zuvor erstellt haben. Auf der **starten** Menü klicken Sie auf **Programme**, **Microsoft Visual Studio 2010 SDK**, **Tools**, und klicken Sie dann **Zurücksetzen der Microsoft Visual Studio 2010 experimentelle Instanz**. Sie können eine beliebige andere DSLs neu erstellen, die Sie erneut verwenden möchten.  
  
     \- oder –  
  
- Wenn eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , deinstallieren sie die Erweiterung, die diese Dateierweiterung verwendet vollständig auf dem Computer installiert wurde. Auf der **Tools** Menü klicken Sie auf **Erweiterungs-Manager**.  
  
### <a name="product-settings-page"></a>Settings-Produktseite  
 **Was ist der Name des Produkts, das die neue domänenspezifische Sprache gehört?**  
 Der Standardwert ist der Name der DSL.  
  
 Dieser Wert wird verwendet, in Windows Explorer (oder Datei-Explorer), um Dateien zu beschreiben, die dieser Dateierweiterung.  
  
 **Was ist der Name des Unternehmens, das das Produkt gehört?**  
 Den Namen Ihres Unternehmens.  
  
 Dieser Wert wird in die AssemblyInfo-Eigenschaften der Ihr DSL-Paket integriert.  
  
 **Was ist der Stammnamespace für Projekte in dieser Lösung?**  
 Dies ist standardmäßig auf einen Namen, die von Ihrem Unternehmen besteht und aus Produktnamen besteht.  
  
### <a name="signing-page"></a>Seite "Signierung"  
 **Erstellen Sie eine Schlüsseldatei mit starkem Namen**  
 Die Standardoption ist, um einen neuen Schlüssel zum Signieren Ihrer DSL-Assembly zu erstellen.  
  
 **Verwenden Sie die vorhandenen Schlüssel mit starkem Namen**  
 Verwenden Sie diese Option, wenn Sie Ihre DSL in einer anderen Assembly integrieren möchten.  
  
 Weitere Informationen zu starken Namen finden Sie unter [erstellen und Assemblys mit starkem Namen](http://go.microsoft.com/fwlink/?LinkId=186073).  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)   
 [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
