---
title: Aktualisieren von benutzerdefinierten Projekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- upgrading project systems
- projects [Visual Studio SDK], upgrading
- project system upgrades [Visual Studio]
ms.assetid: 262ada44-7689-44d8-bacb-9c6d33834d4e
caps.latest.revision: 11
manager: douge
ms.openlocfilehash: 5c3fd31cfc7cfbf3f7dd687d38483f5bb62703ca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515680"
---
# <a name="upgrading-custom-projects"></a>Aktualisieren von benutzerdefinierten Projekten
Wenn Sie die in der Projektdatei dauerhaft gespeicherten Informationen zwischen verschiedenen Visual Studio-Versionen Ihres Produkts ändern, müssen Sie das Durchführen eines Upgrades der Projektdatei von der alten auf die neue Version unterstützen. Zur Unterstützung der aktualisieren, die Ihnen ermöglicht, die Teilnahme an der **Visual Studio-Konvertierungs-Assistenten**, implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Schnittstelle. Diese Schnittstelle stellt das einzige verfügbare Verfahren zum Durchführen von Kopierupgrades dar. Das Upgrade des Projekts erfolgt im Rahmen des Öffnens der Projektmappe. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Schnittstelle wird von der Projektfactory implementiert oder sollte zumindest sein, dass von der Projektfactory.  
  
 Der alte Mechanismus, der verwendet die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Benutzeroberfläche wird weiterhin unterstützt, aber im Prinzip das Upgrade des als Teil des Projekts öffnen. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Schnittstelle wird daher aufgerufen, durch die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Umgebung auch, wenn die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Schnittstelle aufgerufen wird oder implementiert. Dieser Ansatz ermöglicht Ihnen die Verwendung <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> die Kopie zu implementieren und nur Teile des Upgrades zu projizieren und delegieren die restlichen Aufgaben für ein direktes (möglicherweise auf dem neuen Speicherort) ausgeführt werden, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Schnittstelle.  
  
 Eine beispielimplementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, finden Sie unter [VSSDK-Beispiele](../misc/vssdk-samples.md).  
  
 Im Rahmen von Projektupgrades stellen sich die folgenden Szenarien dar:  
  
-   Wenn die Datei ein neueres Format aufweist, als es vom Projekt unterstützt werden kann, muss eine Fehlermeldung zurückgegeben werden, aus der dieser Umstand hervorgeht. Dabei wird vorausgesetzt, dass die ältere Version Ihres Produkts – z. B. Visual Studio .NET 2003 – Code zum Überprüfen der Version enthält.  
  
-   Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> Flag angegeben wird, der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> -Methode, das Upgrade wird als ein direktes Upgrade vor dem Öffnen des Projekts implementiert werden.  
  
-   Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> Flag angegeben wird, der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> -Methode, das Upgrade als kopierupgrade implementiert wird.  
  
-   Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> Flag angegeben wird, der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> aufrufen, und klicken Sie dann der Benutzer von der Umgebung aufgefordert wurde, um ein upgrade der Projektdatei als ein direktes Upgrade, nachdem das Projekt geöffnet wird. Beispielsweise fordert die Umgebung den Benutzer zum Upgrade auf, wenn der Benutzer eine ältere Version der Lösung öffnet.  
  
-   Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> Flag nicht angegeben wird, der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> aufrufen, und klicken Sie dann aufgefordert, den Benutzer zum upgrade der Projektdatei müssen.  
  
     Die folgende Aufforderungsnachricht stellt ein Beispiel dar:  
  
     "Das Projekt '%1' wurde in einer älteren Version von Visual Studio erstellt. Wenn Sie es mit dieser Version von Visual Studio öffnen, können Sie es möglicherweise nicht mehr mit älteren Versionen von Visual Studio öffnen. Möchten Sie fortfahren und dieses Projekt öffnen?"  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>So implementieren Sie IVsProjectUpgradeViaFactory  
  
1.  Implementieren Sie die Methode von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Schnittstelle, insbesondere die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> -Methode in Ihrer projektfactoryimplementierung, oder machen Sie die Implementierungen von Ihrer projektfactoryimplementierung aufgerufen.  
  
2.  Wenn Sie ein direktes Upgrade als Teil des Öffnens der Projektmappe tun möchten, geben Sie das Flag <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> als die `VSPUVF_FLAGS` Parameter in Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Implementierung.  
  
3.  Wenn Sie ein direktes Upgrade als Teil des Öffnens der Projektmappe tun möchten, geben Sie das Flag <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> als die `VSPUVF_FLAGS` Parameter in Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Implementierung.  
  
4.  Für die Schritte 2 und 3, die eigentlichen dateiupgradeschritte, mithilfe von <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, können implementiert werden, wie beschrieben in der "implementieren `IVsProjectUpgade`" weiter unten im Abschnitt, oder Sie können das eigentliche dateiupgrade zu delegieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
5.  Verwenden Sie die Methoden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> beziehen Sie Upgrade veröffentlichen Nachrichten für den Benutzer, die mit Visual Studio-Migrations-Assistenten.  
  
6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> Schnittstelle wird verwendet, um jede Art von dateiupgrade zu implementieren, die im Rahmen eines Projektupgrades erfolgen muss. Diese Schnittstelle wird nicht aufgerufen, von <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, aber möglicherweise nicht direkt über ein Mechanismus, um Dateien zu aktualisieren, die das Projektsystem, aber das Hauptprojekt-System gehören angegeben ist. Diese Situation kann beispielsweise eintreten, wenn die compilerbezogenen Dateien und Eigenschaften nicht vom gleichen Entwicklungsteam wie der Rest des Projektsystems betreut werden.  
  
## <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade-Implementierung  
 Wenn Ihr Projektsystem implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> es kann nur nicht teilnehmen die **Visual Studio-Konvertierungs-Assistenten**. Aber selbst wenn Sie implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> -Schnittstelle, Sie können weiterhin das dateiupgrade zu delegieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Implementierung.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>So implementieren Sie IVsProjectUpgrade  
  
1.  Wenn ein Benutzer versucht, ein Projekt zu öffnen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Methode wird von der Umgebung aufgerufen, nachdem das Projekt geöffnet wurde und bevor andere Benutzeraktionen für das Projekt ausgeführt werden können. Wenn der Benutzer bereits aufgefordert wurde, aktualisieren Sie die Projektmappe, und klicken Sie dann die <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> Flag übergeben die `grfUpgradeFlags` Parameter. Wenn der Benutzer ein Projekt direkt, solche öffnet wie mit der **vorhandenes Projekt hinzufügen** Befehl ein, und klicken Sie dann die <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> Flag nicht übergeben, und das Projekt muss der Benutzer zum upgrade auffordern.  
  
2.  Als Reaktion auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> -Aufruf, ob die Projektdatei aktualisiert wird, muss das Projekt bewerten. Wenn das Projekt muss nicht den Projekttyp auf eine neue Version zu aktualisieren, kann er einfach Zurückgeben der <xref:Microsoft.VisualStudio.VSConstants.S_OK> Flag.  
  
3.  Wenn das Projekt muss den Projekttyp auf eine neue Version zu aktualisieren, muss Sie ermitteln, ob die Projektdatei kann, durch den Aufruf geändert werden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> -Methode und übergeben des Werts der <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> für die `rgfQueryEdit` Parameter. In diesem Fall muss das Projekt folgendes ausführen:  
  
    -   Wenn die `VSQueryEditResult` zurückgegebene Wert in der `pfEditCanceled` Parameter <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>, und klicken Sie dann das Upgrade fortgesetzt werden kann, weil die Projektdatei geschrieben werden kann.  
  
    -   Wenn die `VSQueryEditResult` zurückgegebene Wert in der `pfEditCanceled` -Parameter ist <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> und `VSQueryEditResult` Wert hat die <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> -Bit festgelegt ist, klicken Sie dann <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> muss einen Fehler zurückgeben, da der Benutzer das Berechtigungsproblem selbst lösen müssen. Das Projekt sollte dann Folgendes ausführen:  
  
         Melden Sie den Fehler an den Benutzer durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>. und Zurückgeben der <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> Fehlercode <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
    -   Wenn die `VSQueryEditResult` Wert <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> und `VSQueryEditResultFlags` Wert hat die <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> -Bit festgelegt ist, aus, und klicken Sie dann die Projektdatei durch Aufrufen von ausgecheckt werden <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>,...).  
  
4.  Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> Aufruf auf die Projektdatei führt dazu, dass die Datei ausgecheckt werden, und die neueste Version abgerufen werden sollen, und klicken Sie dann das Projekt entladen und neu geladen wird. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> -Methode erneut aufgerufen, nachdem eine andere Instanz des Projekts erstellt wurde. Bei diesem zweiten Aufruf kann die Projektdatei auf den Datenträger geschrieben werden; es wird empfohlen, dass das Projekt eine Kopie der Projektdatei im vorherigen Format mit einer OLD-Erweiterung speichert, die für das Upgrade erforderlichen Änderungen vornimmt und die Projektdatei anschließend im neuen Format speichert. Erneut, wenn Sie einen beliebigen Teil des Upgradevorgangs ein Fehler auftritt, die Methode muss geben Fehler durch Zurückgeben von <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>. Dadurch wird das Projekt aus dem Projektmappen-Explorer entladen.  
  
     Es ist wichtig, den vollständigen Prozess zu verstehen, die in der Umgebung für den Fall, in dem tritt auf, den Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> Methodenrückgabe (dabei den Wert "reportonly") der <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> und <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> Flags.  
  
5.  Der Benutzer versucht, die Projektdatei zu öffnen.  
  
6.  Die Umgebung ruft Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> Implementierung.  
  
7.  Wenn <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> gibt `true`, und klicken Sie dann die Umgebung ruft Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> Implementierung.  
  
8.  Die Umgebung ruft Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> Implementierung so öffnen Sie die Datei, und initialisieren Sie das Projektobjekt, z. B. Project1 ab.  
  
9. Die Umgebung ruft Ihre `IVsProjectUpgrade::UpgradeProject` -Implementierung auf, um zu bestimmen, ob ein Upgrade der Projektdatei erforderlich ist.  
  
10. Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> und übergeben Sie einen Wert von <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> für die `rgfQueryEdit` Parameter.  
  
11. Gibt die Umgebung <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> für `VSQueryEditResult` und <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> Bit ist gesetzt, `VSQueryEditResultFlags`.  
  
12. Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Standardimplementierung ruft `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>).  
  
 Dieser Aufruf kann dazu führen, dass eine neue Kopie Ihrer Projektdatei ausgecheckt und die neueste Version abgerufen wird, wodurch es erforderlich wird, die Projektdatei neu zu laden. An diesem Punkt geschieht eins von zwei Dingen:  
  
-   Wenn Sie Ihre eigenen erneute Laden des Projekts behandelt, klicken Sie dann die Umgebung ruft Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> -Implementierung (VSITEMID_ROOT). Wenn Sie diesen Aufruf empfangen, laden Sie die erste Instanz des Projekts (Projekt1) erneut, und fahren Sie mit dem Upgrade Ihrer Projektdatei fort. Die Umgebung weiß, dass Sie Ihre eigenen erneute Laden des Projekts behandeln, wenn Sie zurückkehren `true` für <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>).  
  
-   Wenn Sie zurückkehren, behandeln Sie keine eigene erneute Laden des Projekts `false` für <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>). In diesem Fall vor dem <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>([QEF_ForceEdit_NoPrompting](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True), [QEF_DisallowInMemoryEdits](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True),) zurückgibt, erstellt die Umgebung als eine weitere neue Instanz des Projekts, z. B. "Projekt2", Die folgende:  
  
    1.  Die Umgebung ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> in Ihr erstes Projektobjekt Projekt1, platzieren Sie daher dieses Objekt in den inaktiven Status.  
  
    2.  Die Umgebung ruft Ihre `IVsProjectFactory::CreateProject` -Implementierung auf, um eine zweite Instanz Ihres Projekts zu erstellen, „Project2“.  
  
    3.  Die Umgebung ruft Ihre `IPersistFileFormat::Load` -Implementierung auf, um die Datei zu öffnen und das zweite Projektobjekt, „Projekt2“, zu initialisieren.  
  
    4.  Die Umgebung ruft `IVsProjectUpgrade::UpgradeProject` ein zweites Mal auf, um zu bestimmen, ob für das Projektobjekt ein Upgrade ausgeführt werden soll. Dieser Aufruf erfolgt jedoch für eine neue, zweite Instanz des Projekts, „Projekt2“. Dies ist das Projekt, das in der Projektmappe geöffnet ist.  
  
        > [!NOTE]
        >  In der Instanz, die Ihr erste Projekt Project1 befindet sich in den inaktiven Status, und Sie müssen zurückgeben <xref:Microsoft.VisualStudio.VSConstants.S_OK> aus dem ersten Aufruf von Ihrem <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Implementierung. Finden Sie unter [Basisprojekt](http://msdn.microsoft.com/en-us/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) für eine Implementierung der `IVsProjectUpgrade::UpgradeProject`.  
  
    5.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> und übergeben Sie einen Wert von <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> für die `rgfQueryEdit` Parameter.  
  
    6.  Gibt die Umgebung <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> und das Upgrade kann fortgesetzt werden, weil die Projektdatei geschrieben werden kann.  
  
 Wenn Sie nicht aktualisieren, zurück <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> aus `IVsProjectUpgrade::UpgradeProject`. Wenn für Sie kein Upgrade erforderlich ist oder Sie sich gegen das Upgrade entscheiden, behandeln Sie den `IVsProjectUpgrade::UpgradeProject` -Aufruf als nicht erfolgten Vorgang (No-Op). Wenn Sie zurückkehren <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>, mit der Lösung für Ihr Projekt ein Platzhalterknoten hinzugefügt.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Konvertierungs-Assistenten](http://msdn.microsoft.com/en-us/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Aktualisieren von Projektelementen](../misc/upgrading-project-items.md)   
 [Projekte](../extensibility/internals/projects.md)