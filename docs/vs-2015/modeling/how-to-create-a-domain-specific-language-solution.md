---
title: 'Vorgehensweise: Erstellen einer domänenspezifischen Sprachlösung | Microsoft-Dokumentation'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 60813fcce28c71c91a3e0c2af9889261c8897a99
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301413"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Gewusst wie: Erstellen einer domänenspezifischen Sprachlösung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine domänenspezifische Sprache (DSL) wird mithilfe einer spezialisierten [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Lösung erstellt.

## <a name="prerequisites"></a>Erforderliche Komponenten
 Bevor Sie dieses Verfahren starten können, müssen Sie zunächst die folgenden Komponenten installieren:

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](https://go.microsoft.com/fwlink/?LinkID=185579)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](https://go.microsoft.com/fwlink/?LinkID=185580)|
|Visual Studio Visualization and Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=185581](https://go.microsoft.com/fwlink/?LinkID=185581)|

## <a name="creating-a-domain-specific-language-solution"></a>Erstellen einer domänenspezifischen Sprachlösung

#### <a name="to-create-a-domain-specific-language-solution"></a>So erstellen Sie eine domänenspezifische Sprachlösung

1. Starten Sie den DSL-Assistenten.

   1. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

   2. Das Dialogfeld **Neues Projekt** wird angezeigt.

   3. Erweitern Sie unter **Projekttypen**den Knoten **andere Projekttypen** , und klicken Sie auf **Erweiterbarkeit**.

   4. Klicken Sie auf **Domänen spezifischer sprach-Designer**.

   5. Geben Sie im Feld **Name** einen Namen für die Projekt Mappe ein. Klicken Sie auf **OK**.

       Der **Assistent für das domänenspezifische sprach-Designer** wird angezeigt.

      > [!NOTE]
      > Vorzugsweise sollte der Name, den Sie eingeben, ein gültiger C# visueller Bezeichner sein, da er zum Generieren von Code verwendet werden kann.

      ![DSL-Dialogfeld erstellen](../modeling/media/create-dsldialog.png "Create_DSLDialog")

2. Wählen Sie eine DSL-Vorlage aus.

    Wählen Sie auf der Seite **Optionen für domänenspezifische Sprache auswählen** eine der Lösungs Vorlagen aus, z. b. **minimale Sprache**. Wählen Sie eine Vorlage aus, die der zu erstellenden DSL ähnelt.

    Weitere Informationen zu Lösungs Vorlagen finden Sie unter [Auswählen einer Lösungs Vorlage für eine domänenspezifische Sprache](../modeling/choosing-a-domain-specific-language-solution-template.md).

3. Geben Sie auf der Seite **Dateierweiterung** eine Dateierweiterung ein. Sie muss auf Ihrem Computer und auf allen Computern, auf denen Sie die DSL installieren möchten, eindeutig sein. Die Meldung " **keine Anwendungen oder Visual Studio-Editoren" sollte diese Erweiterung verwenden**.

   - Wenn Sie die Dateinamenerweiterung in früheren experimentellen DSLs verwendet haben, die noch nicht vollständig installiert wurden, können Sie Sie mit dem Tool " **experimentelle Instanz zurücksetzen** " löschen, das sich im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] SDK-Menü befindet.

   - Wenn eine andere [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Erweiterung, die diese Dateierweiterung verwendet, vollständig auf dem Computer installiert wurde, sollten Sie diese deinstallieren. Klicken Sie **im Menü Extras** auf **Erweiterungs-Manager**.

4. Überprüfen Sie die Felder auf den verbleibenden Seiten des Assistenten, und passen Sie Sie ggf. an. Wenn Sie mit den Einstellungen zufrieden sind, klicken Sie auf **Fertig**stellen. Weitere Informationen zu den Einstellungen finden Sie unter [DSL-Designer-Assistenten Seiten](#settings).

    Der Assistent erstellt eine Projekt Mappe mit zwei Projekten namens **DSL** und **dslpackage**.

   > [!NOTE]
   > Wenn eine Meldung angezeigt wird, dass keine Textvorlagen aus nicht vertrauenswürdigen Quellen ausgeführt werden sollen, klicken Sie auf **OK**. Diese Meldung kann so festgelegt werden, dass Sie nicht erneut angezeigt wird.

## <a name="settings"></a>Die Seiten des DSL-Designer-Assistenten
 Sie können einige der Felder unverändert lassen, um die Standardwerte zu ändern. Stellen Sie jedoch sicher, dass Sie das Feld Dateierweiterung festgelegt haben.

### <a name="solution-settings-page"></a>Seite "Lösungs Einstellungen"
 **Auf welcher Vorlage möchten Sie Ihre domänenspezifische Sprache aufbauen?**
Wählen Sie eine Vorlage aus, die der zu erstellenden DSL ähnelt. Die verschiedenen Vorlagen bieten praktische Ausgangspunkte. Wenn Sie eine Projektmappenvorlage auswählen, zeigt der Assistent eine Beschreibung an. Weitere Informationen zu Lösungs Vorlagen finden Sie unter [Auswählen einer Lösungs Vorlage für eine domänenspezifische Sprache](../modeling/choosing-a-domain-specific-language-solution-template.md).

 **Wie möchten Sie Ihre domänenspezifische Sprache benennen?**
Der Standardwert ist der Projektmappenname. Der Code wird aus diesem Wert generiert. Er muss als C# Klassenname gültig sein.

### <a name="file-extension-page"></a>Datei Erweiterungs Seite
 **Welche Erweiterung sollen Modelldateien verwenden?**
Geben Sie eine neue Dateierweiterung ein.

 Vergewissern Sie sich, dass diese Dateierweiterung nicht bereits für die Verwendung auf diesem Computer registriert wurde. gehen Sie hierzu wie folgt vor:

 Sehen **Sie sich die anderen Tools und Anwendungen an, die für diese Erweiterung registriert**sind. Wenn die Meldung " **keine Anwendungen oder Visual Studio-Editoren verwenden diese Erweiterung**" angezeigt wird, können Sie diese Dateierweiterung verwenden.

 Wenn eine Liste der Tools oder Pakete angezeigt wird, sollten Sie eine der folgenden Aktionen ausführen:

- Geben Sie eine andere Dateierweiterung ein.

     \- oder –

- Setzen Sie den [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] experimentellen Instanz zurück. Dadurch wird die Registrierung aller zuvor erstellten DSLs aufgehoben. Klicken Sie im **Startmenü** auf **Alle Programme**, **Microsoft Visual Studio 2010 SDK**, **Tools**, und setzen Sie dann **die experimentelle Microsoft Visual Studio 2010-Instanz zurück**. Sie können alle anderen DSLs neu erstellen, die Sie wieder verwenden möchten.

     \- oder –

- Wenn eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Erweiterung, die diese Dateierweiterung verwendet, vollständig auf dem Computer installiert wurde, deinstallieren Sie Sie. Klicken Sie **im Menü Extras** auf **Erweiterungs-Manager**.

### <a name="product-settings-page"></a>Seite "Produkt Einstellungen"
 **Wie lautet der Name des Produkts, zu dem die neue domänenspezifische Sprache gehört?**
Der Standardwert ist der DSL-Name.

 Dieser Wert wird im Windows-Explorer (oder Datei-Explorer) verwendet, um Dateien zu beschreiben, die diese Dateierweiterung aufweisen.

 **Wie lautet der Name des Unternehmens, zu dem das Produkt gehört?**
Der Name Ihres Unternehmens.

 Dieser Wert ist in die AssemblyInfo-Eigenschaften Ihres DSL-Pakets integriert.

 **Was ist der Stamm Namespace für Projekte in dieser Projekt Mappe?**
Standardmäßig wird ein Name verwendet, der aus Ihrem Unternehmen und ihren Produktnamen besteht.

### <a name="signing-page"></a>Signierungs Seite
 **Erstellen einer Schlüsseldatei mit starkem Namen** Die Standardoption besteht darin, einen neuen Schlüssel zum Signieren Ihrer DSL-Assembly zu erstellen.

 **Vorhandenen Schlüssel mit starkem Namen verwenden** Verwenden Sie diese Option, wenn Sie Ihre DSL in eine andere Assembly integrieren möchten.

 Weitere Informationen zu starken Namen finden Sie unter [Erstellen und verwenden](https://go.microsoft.com/fwlink/?LinkId=186073)von Assemblys mit starkem Namen.

## <a name="see-also"></a>Siehe auch
 [Definieren einer domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md) [DSL-Tools Glossar](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
