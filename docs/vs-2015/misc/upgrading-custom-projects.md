---
title: Aktualisieren von benutzerdefinierten Projekten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- upgrading project systems
- projects [Visual Studio SDK], upgrading
- project system upgrades [Visual Studio]
ms.assetid: 262ada44-7689-44d8-bacb-9c6d33834d4e
caps.latest.revision: 11
manager: jillfra
ms.openlocfilehash: f9d930765a427d32836f464a424b5cd898090ac5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436531"
---
# <a name="upgrading-custom-projects"></a>Aktualisieren von benutzerdefinierten Projekten
Wenn Sie die in der Projektdatei dauerhaft gespeicherten Informationen zwischen verschiedenen Visual Studio-Versionen Ihres Produkts ändern, müssen Sie das Durchführen eines Upgrades der Projektdatei von der alten auf die neue Version unterstützen. Zur Unterstützung der aktualisieren, die Ihnen ermöglicht, die Teilnahme an der **Visual Studio-Konvertierungs-Assistenten**, implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Schnittstelle. Diese Schnittstelle stellt das einzige verfügbare Verfahren zum Durchführen von Kopierupgrades dar. Das Upgrade des Projekts erfolgt im Rahmen des Öffnens der Projektmappe. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>-Schnittstelle wird von der Projektfactory implementiert oder sollte zumindest über diese verfügbar sein.  
  
 Der alte Mechanismus, der die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>-Schnittstelle verwendet, wird noch unterstützt, doch wird dabei das abweichende Konzept verfolgt, das Upgrade des Projektsystems beim Öffnen des Projekts vorzunehmen. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>-Schnittstelle wird daher von der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Umgebung auch dann aufgerufen, wenn die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>-Schnittstelle aufgerufen wird oder implementiert ist. Aufgrund dieses Ansatzes können Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> verwenden, um die Kopie zu implementieren und nur Teile des Upgrades zu projizieren, wobei der Rest der Arbeit für die Ausführung an Ort und Stelle (also möglichst dem neuen Speicherort) durch die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>-Schnittstelle delegiert wird.  
  
 Eine beispielimplementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, finden Sie unter [VSSDK-Beispiele](../misc/vssdk-samples.md).  
  
 Im Rahmen von Projektupgrades stellen sich die folgenden Szenarien dar:  
  
- Wenn die Datei ein neueres Format aufweist, als es vom Projekt unterstützt werden kann, muss eine Fehlermeldung zurückgegeben werden, aus der dieser Umstand hervorgeht. Dabei wird vorausgesetzt, dass die ältere Version Ihres Produkts – z. B. Visual Studio .NET 2003 – Code zum Überprüfen der Version enthält.  
  
- Wenn das <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>-Flag in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>-Methode angegeben ist, wird das Upgrade vor dem Öffnen des Projekts als Upgrade an Ort und Stelle ausgeführt.  
  
- Wenn das <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>-Flag in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>-Methode angegeben ist, wird das Upgrade als Kopierupgrade implementiert.  
  
- Wenn das <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>-Flag im <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>-Aufruf angegeben ist, wurde der Benutzer von der Umgebung aufgefordert, nach dem Öffnen des Projekts ein Upgrade der Projektdatei an Ort und Stelle auszuführen. Beispielsweise fordert die Umgebung den Benutzer zum Upgrade auf, wenn der Benutzer eine ältere Version der Lösung öffnet.  
  
- Wenn das <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>-Flag nicht im <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>-Aufruf angegeben ist, müssen Sie den Benutzer auffordern, ein Upgrade der Projektdatei auszuführen.  
  
     Die folgende Aufforderungsnachricht stellt ein Beispiel dar:  
  
     "Das Projekt '%1' wurde in einer älteren Version von Visual Studio erstellt. Wenn Sie es mit dieser Version von Visual Studio öffnen, können Sie es möglicherweise nicht mehr mit älteren Versionen von Visual Studio öffnen. Möchten Sie fortfahren und dieses Projekt öffnen?"  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>So implementieren Sie IVsProjectUpgradeViaFactory  
  
1. Implementieren Sie die Methode der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>-Schnittstelle, insbesondere die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>-Methode in Ihrer Projektfactoryimplementierung, oder machen Sie die Implementierungen von Ihrer Projektfactoryimplementierung aus aufrufbar.  
  
2. Wenn Sie ein Upgrade an Ort und Stelle als Teil des Öffnens der Projektmappe ausführen möchten, geben Sie das Flag <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> als Parameter von `VSPUVF_FLAGS` in Ihrer <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>-Implementierung an.  
  
3. Wenn Sie ein Upgrade an Ort und Stelle als Teil des Öffnens der Projektmappe ausführen möchten, geben Sie das Flag <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> als Parameter von `VSPUVF_FLAGS` in Ihrer <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>-Implementierung an.  
  
4. Für die Schritte 2 und 3, die eigentlichen Dateiupgradeschritte, kann die Verwendung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> wie im Abschnitt "Implementierung von `IVsProjectUpgade`" im Abschnitt unten beschrieben implementiert werden; alternativ können Sie das eigentliche Dateiupgrade an <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> delegieren.  
  
5. Verwenden Sie die Methoden von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>, um mit Upgrades zusammenhängende Nachrichten für Benutzer mithilfe des Visual Studio-Migrations-Assistenten zu veröffentlichen.  
  
6. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade>-Schnittstelle wird verwendet, um jede Art von Dateiupgrade zu implementieren, die im Rahmen eines Projektupgrades erfolgen muss. Diese Schnittstelle wird nicht von <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> aufgerufen, sondern als Mechanismus für das Upgrade von Dateien bereitgestellt, die zum Projektsystem gehören, von denen das Projekthauptsystem jedoch möglicherweise keine unmittelbare Kenntnis hat. Diese Situation kann beispielsweise eintreten, wenn die compilerbezogenen Dateien und Eigenschaften nicht vom gleichen Entwicklungsteam wie der Rest des Projektsystems betreut werden.  
  
## <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade-Implementierung  
 Wenn Ihr Projektsystem implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> es kann nur nicht teilnehmen die **Visual Studio-Konvertierungs-Assistenten**. Aber selbst wenn Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>-Schnittstelle implementieren, können Sie das Dateiupgrade trotzdem an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>-Implementierung delegieren.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>So implementieren Sie IVsProjectUpgrade  
  
1. Wenn ein Benutzer versucht, ein Projekt zu öffnen, wird die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>-Methode von der Umgebung aufgerufen, nachdem das Projekt geöffnet wurde und bevor andere Benutzeraktionen für das Projekt ausgeführt werden können. Wenn der Benutzer bereits aufgefordert wurde, ein Upgrade der Projektmappe auszuführen, wird im `grfUpgradeFlags`-Parameter das <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>-Flag übergeben. Wenn der Benutzer ein Projekt direkt, solche öffnet wie mit der **vorhandenes Projekt hinzufügen** Befehl ein, und klicken Sie dann die <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> Flag nicht übergeben, und das Projekt muss der Benutzer zum upgrade auffordern.  
  
2. In Reaktion auf den <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>-Aufruf muss das Projekt bewerten, ob für die Projektdatei ein Upgrade ausgeführt werden muss. Wenn das Projekt für den Projekttyp kein Upgrade auf eine neue Version ausführen muss, kann es einfach das <xref:Microsoft.VisualStudio.VSConstants.S_OK>-Flag zurückgeben.  
  
3. Wenn das Projekt ein Upgrade des Projekttyps auf eine neue Version vornehmen muss, muss es bestimmen, ob die Projektdatei durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>-Methode und Übergeben des Werts <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> für den `rgfQueryEdit`-Parameter geändert werden kann. In diesem Fall muss das Projekt folgendes ausführen:  
  
   - Wenn der im `pfEditCanceled`-Parameter zurückgegebene `VSQueryEditResult`-Wert <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> ist, kann das Upgrade fortgesetzt werden, weil die Projektdatei geschrieben werden kann.  
  
   - Wenn der im `pfEditCanceled`-Parameter zurückgegebene `VSQueryEditResult`-Wert <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> ist und für den `VSQueryEditResult`-Wert das <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>-Bit festgelegt ist, muss <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> einen Fehler zurückgeben, da der Benutzer das Berechtigungsproblem selbst lösen muss. Das Projekt sollte dann Folgendes ausführen:  
  
        Durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> dem Benutzer den Fehler melden und den <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>-Fehlercode an <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> zurückgeben.  
  
   - Wenn der `VSQueryEditResult`-Wert <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> ist und für den `VSQueryEditResultFlags`-Wert das <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>-Bit festgelegt ist, sollte die Projektdatei durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>,...) ausgecheckt werden.  
  
4. Wenn der <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>-Aufruf der Projektdateien zum Auschecken der Datei und zum Abrufen der letzten Version führt, wird das Projekt entladen und erneut geladen. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>-Methode wird erneut aufgerufen, sobald eine weitere Instanz des Projekts erstellt wird. Bei diesem zweiten Aufruf kann die Projektdatei auf den Datenträger geschrieben werden; es wird empfohlen, dass das Projekt eine Kopie der Projektdatei im vorherigen Format mit einer OLD-Erweiterung speichert, die für das Upgrade erforderlichen Änderungen vornimmt und die Projektdatei anschließend im neuen Format speichert. Wenn bei irgendeinem Teil des Upgradevorgangs ein Fehler auftritt muss auch hier die Methode den Fehler durch Zurückgeben von <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> anzeigen. Dadurch wird das Projekt aus dem Projektmappen-Explorer entladen.  
  
    Für den Fall, dass der Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>-Methode (mit dem Wert „ReportOnly“) die Flags <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> und <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> zurückgibt, ist es wichtig, den gesamten Prozess zu verstehen, der in der Umgebung geschieht.  
  
5. Der Benutzer versucht, die Projektdatei zu öffnen.  
  
6. Die Umgebung ruft Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>-Implementierung auf.  
  
7. Wenn <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> `true` zurückgibt, ruft die Umgebung Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>-Implementierung auf.  
  
8. Die Umgebung ruft Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A>-Implementierung auf, um die Datei zu öffnen und das Projektobjekt zu initialisieren z. B. „Projekt1“.  
  
9. Die Umgebung ruft Ihre `IVsProjectUpgrade::UpgradeProject` -Implementierung auf, um zu bestimmen, ob ein Upgrade der Projektdatei erforderlich ist.  
  
10. Sie rufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> auf und übergeben den Wert <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> für den `rgfQueryEdit`-Parameter.  
  
11. Die Umgebung gibt für `VSQueryEditResult` den Wert <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> zurück, und in `VSQueryEditResultFlags` wird das <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>-Bit festgelegt.  
  
12. Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>-Implementierung ruft `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>) auf.  
  
    Dieser Aufruf kann dazu führen, dass eine neue Kopie Ihrer Projektdatei ausgecheckt und die neueste Version abgerufen wird, wodurch es erforderlich wird, die Projektdatei neu zu laden. An diesem Punkt geschieht eins von zwei Dingen:  
  
- Wenn Sie das erneute Laden des Projekts selbst vornehmen, ruft die Umgebung Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>-Implementierung (VSITEMID_ROOT) auf. Wenn Sie diesen Aufruf empfangen, laden Sie die erste Instanz des Projekts (Projekt1) erneut, und fahren Sie mit dem Upgrade Ihrer Projektdatei fort. Die Umgebung weiß, dass Sie das erneute Laden des Projekts selbst übernehmen, wenn Sie für <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>) `true` zurückgeben.  
  
- Wenn Sie das erneute Laden des Projekts nicht selbst ausführen, geben Sie für <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>) `false` zurück. In diesem Fall vor dem <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>([QEF_ForceEdit_NoPrompting](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True), [QEF_DisallowInMemoryEdits](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True),) zurückgibt, erstellt die Umgebung als eine weitere neue Instanz des Projekts, z. B. "Projekt2", Die folgende:  
  
  1. Die Umgebung ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> für Ihr erstes Projektobjekt „Project1“ auf und versetzt dieses Objekt dadurch in den inaktiven Zustand.  
  
  2. Die Umgebung ruft Ihre `IVsProjectFactory::CreateProject` -Implementierung auf, um eine zweite Instanz Ihres Projekts zu erstellen, „Project2“.  
  
  3. Die Umgebung ruft Ihre `IPersistFileFormat::Load` -Implementierung auf, um die Datei zu öffnen und das zweite Projektobjekt, „Projekt2“, zu initialisieren.  
  
  4. Die Umgebung ruft `IVsProjectUpgrade::UpgradeProject` ein zweites Mal auf, um zu bestimmen, ob für das Projektobjekt ein Upgrade ausgeführt werden soll. Dieser Aufruf erfolgt jedoch für eine neue, zweite Instanz des Projekts, „Projekt2“. Dies ist das Projekt, das in der Projektmappe geöffnet ist.  
  
      > [!NOTE]
      > Wenn die Instanz Ihres ersten Projekts, „Projekt1“, in den inaktiven Status versetzt wurde, müssen Sie vom ersten Aufruf <xref:Microsoft.VisualStudio.VSConstants.S_OK> an Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>-Implementierung zurückgeben. Eine Implementierung von [IVsProjectUpgrade::UpgradeProject](http://msdn.microsoft.com/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) finden Sie unter `IVsProjectUpgrade::UpgradeProject`.  
  
  5. Sie rufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> auf und übergeben den Wert <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> für den `rgfQueryEdit`-Parameter.  
  
  6. Die Umgebung gibt <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> zurück, und das Upgrade kann fortgesetzt werden, weil die Projektdatei geschrieben werden kann.  
  
  Wenn Sie das Upgrade versäumen, geben Sie <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> aus `IVsProjectUpgrade::UpgradeProject` zurück. Wenn für Sie kein Upgrade erforderlich ist oder Sie sich gegen das Upgrade entscheiden, behandeln Sie den `IVsProjectUpgrade::UpgradeProject` -Aufruf als nicht erfolgten Vorgang (No-Op). Wenn Sie <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> zurückgeben, wird dem Projektmappe für Ihr Projekt ein Platzhalterknoten hinzugefügt.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Konvertierungs-Assistenten](http://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Aktualisieren von Projektelementen](../misc/upgrading-project-items.md)   
 [Projekte](../extensibility/internals/projects.md)