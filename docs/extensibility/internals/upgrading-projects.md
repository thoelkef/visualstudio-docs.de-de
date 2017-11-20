---
title: Aktualisieren von Projekten | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ed049293c50fc59c7f6541a3b4a4cc58c6bd5a7b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="upgrading-projects"></a>Aktualisieren von Projekten
Ändert eine Version der in das Projektmodell [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zur nächsten erfordern, dass Projekte und Projektmappen aktualisiert werden, sodass sie auf die neuere Version ausgeführt werden können. Die [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] stellt Schnittstellen, die zum Implementieren von upgradeunterstützung in Ihren eigenen Projekten verwendet werden können.  
  
## <a name="upgrade-strategies"></a>Aktualisierungsstrategien  
 Um ein Upgrade zu unterstützen, muss die Implementierung der Projekt-System definieren und implementieren eine Aktualisierungsstrategie. Beim Bestimmen der Strategie, können Sie zur Unterstützung von Seite-an-Seite (SxS) Sicherung oder kopiesicherung auswählen.  
  
-   SxS-Sicherung bedeutet, dass ein Projekt nur die Dateien kopiert, für die Aktualisierung direkt in einen geeigneten Namen Dateisuffixes, z. B. hinzufügen ".old" erforderlich.  
  
-   Kopiesicherung bedeutet, dass ein Projekt alle Projektelemente in einem vom Benutzer bereitgestellte Sicherungsspeicherort kopiert. Die relevanten Dateien am ursprünglichen Projektspeicherort werden anschließend aktualisiert.  
  
## <a name="how-upgrade-works"></a>Zum Aktualisieren von Works  
 Wenn eine Projektmappe erstellt, die in einer früheren Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wird geöffnet, in einer neueren Version, die IDE-Überprüfungen, die die Projektmappendatei, um festzustellen, ob er muss aktualisiert werden. Wenn ein Upgrade erforderlich ist, ist die **Aktualisierungs-Assistenten** wird automatisch gestartet, um den Benutzer durch den Upgradevorgang zu durchlaufen.  
  
 Wenn eine Lösung aktualisieren müssen, fragt sie jede Factory Projekt für ihre Aktualisierungsstrategie ab. Die Strategie bestimmt, ob die Factory Projekt kopieren oder SxS-Sicherung unterstützt. Die Informationen werden gesendet, um die **Aktualisierungs-Assistenten**, die für die Sicherung erforderliche Informationen erfasst und stellt dem Benutzer die entsprechenden Optionen.  
  
### <a name="multi-project-solutions"></a>Projektmappen mit mehreren Projekten  
 Wenn eine Projektmappe mehrere Projekte enthält, und die Aktualisierungsstrategien unterschiedlich sind, z. B. beim Erstellen eines C++-Projekts, das nur SxS-Sicherung unterstützt und ein Webprojekt, die nur Sicherung kopieren unterstützt, die projektfactorys der Aktualisierungsstrategie ausgehandelt werden müssen.  
  
 Die Lösung fragt jede Factory Projekt für <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Er ruft dann <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> festzustellen, ob die globale Projektdateien aktualisieren benötigen und unterstützten Aktualisierungsstrategien zu bestimmen. Die **Aktualisierungs-Assistenten** wird dann aufgerufen.  
  
 Nach Abschluss des Assistenten, durch der Benutzer <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> für jede Factory Projekt, das tatsächliche Upgrade ausführen aufgerufen wird. Zur Durchführung der Sicherung IVsProjectUpgradeViaFactory Methoden bereit, die <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> Dienst, der die Details des Upgradevorgangs protokollieren. Dieser Dienst kann nicht zwischengespeichert werden.  
  
 Aktualisieren Sie alle relevante globalen Dateien, kann jede Factory Projekt beim Instanziieren eines Projekts auswählen. Muss das Projekt Implementierung unterstützen <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Methode wird aufgerufen, um alle relevanten Projektelemente zu aktualisieren.  
  
> [!NOTE]
>  Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Methode bietet keine SVsUpgradeLogger-Dienst. Dieser Dienst abgerufen werden kann, durch den Aufruf <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.  
  
## <a name="best-practices"></a>Bewährte Methoden  
 Verwenden der <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> Dienst zum Überprüfen, ob Sie können vor der Bearbeitung eine Datei bearbeiten, und vor dem Speichern speichern können. Dies hilft Ihrer Sicherung aus, und aktualisieren Implementierungen behandeln, Projektdateien in der quellcodeverwaltung, Dateien mit unzureichenden Berechtigungen usw..  
  
 Verwenden der <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> service in allen Phasen der Sicherung und aktualisieren, um Informationen zu den Erfolg oder Misserfolg des Upgradevorgangs bereitzustellen.  
  
 Weitere Informationen zum Sichern und Aktualisieren von Projekten finden Sie unter die Kommentare für IVsProjectUpgrade in vsshell2.idl.  
  
## <a name="upgrading-custom-projects"></a>Aktualisieren von benutzerdefinierten Projekten
Wenn Sie die in der Projektdatei dauerhaft gespeicherten Informationen zwischen verschiedenen Visual Studio-Versionen Ihres Produkts ändern, müssen Sie das Durchführen eines Upgrades der Projektdatei von der alten auf die neue Version unterstützen. Zur Unterstützung der aktualisieren, die Ihnen ermöglicht, die Teilnahme an der **Visual Studio-Konvertierungs-Assistenten**, implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Schnittstelle. Diese Schnittstelle stellt das einzige verfügbare Verfahren zum Durchführen von Kopierupgrades dar. Das Upgrade des Projekts erfolgt im Rahmen des Öffnens der Projektmappe. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Schnittstelle wird von der Factory Projekt implementiert oder sollte vom Werk Projekt mindestens erhältlich sein.  
  
 Der alte Mechanismus, verwendet die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Schnittstelle wird weiterhin unterstützt, jedoch grundsätzlich aktualisiert das Projektsystem als Teil des Projekts öffnen. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Schnittstelle wird daher von aufgerufen, die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung erstellen, selbst wenn die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> -Schnittstelle aufgerufen wird oder implementiert. Dieser Ansatz ermöglicht Ihnen die Verwendung <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Projekt nur Teile des Upgrades, implementieren die Kopie und Delegieren der Rest der Arbeit direktes (möglicherweise in den neuen Speicherort) durchgeführt werden, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Schnittstelle.  
  
 Eine beispielimplementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, finden Sie unter [VSSDK-Beispiele](http://aka.ms/vs2015sdksamples).  
  
 Im Rahmen von Projektupgrades stellen sich die folgenden Szenarien dar:  
  
-   Wenn die Datei ein neueres Format aufweist, als es vom Projekt unterstützt werden kann, muss eine Fehlermeldung zurückgegeben werden, aus der dieser Umstand hervorgeht. Dies setzt voraus, dass die ältere Version Ihres Produkts Code zum Überprüfen der Versions enthält.  
  
-   Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> Flag angegeben wird, der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> -Methode, führt das Upgrade als ein direktes Upgrade vor dem Öffnen des Projekts implementiert werden.  
  
-   Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> Flag angegeben wird, der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> -Methode, das Upgrade als kopierupgrade implementiert wird.  
  
-   Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> Flag angegeben wird, der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> aufrufen, wird der Benutzer von der Umgebung aufgefordert wurde, an die Projektdatei als ein direktes Upgrade zu aktualisieren, nachdem das Projekt geöffnet wird. Beispielsweise fordert die Umgebung den Benutzer zum Upgrade auf, wenn der Benutzer eine ältere Version der Lösung öffnet.  
  
-   Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> Flag nicht angegeben ist, der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> aufzurufen, und klicken Sie dann den Benutzer zum upgrade der Projektdatei aufgefordert werden muss.  
  
     Die folgende Aufforderungsnachricht stellt ein Beispiel dar:  
  
     "Das Projekt '%1' wurde in einer älteren Version von Visual Studio erstellt. Wenn Sie es mit dieser Version von Visual Studio öffnen, können Sie es möglicherweise nicht mehr mit älteren Versionen von Visual Studio öffnen. Möchten Sie fortfahren und dieses Projekt öffnen?"  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>So implementieren Sie IVsProjectUpgradeViaFactory  
  
1.  Implementieren Sie die Methode von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Schnittstelle, insbesondere die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Methode in Ihrer projektfactoryimplementierung, oder machen Sie die Implementierungen aus Ihrer projektfactoryimplementierung aufgerufen werden kann.  
  
2.  Wenn Sie als Teil des Öffnens der Projektmappe ein direktes Upgrade ausführen möchten, geben Sie das Flag <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> als die `VSPUVF_FLAGS` Parameter in Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Implementierung.  
  
3.  Wenn Sie als Teil des Öffnens der Projektmappe ein direktes Upgrade ausführen möchten, geben Sie das Flag <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> als die `VSPUVF_FLAGS` Parameter in Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Implementierung.  
  
4.  Für die Schritte 2 und 3, die eigentlichen dateiupgradeschritte, mit <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, implementiert werden können, wie beschrieben in der "implementieren `IVsProjectUpgade`" im folgenden Abschnitt, oder Sie können das eigentliche dateiupgrade zu delegieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
5.  Verwenden Sie die Methoden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> Upgrade buchen bezogene Nachrichten für den Benutzer, die mit Visual Studio-Paketmigrations-Assistenten.  
  
6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade>Schnittstelle wird verwendet, um jede Art von dateiupgrade zu implementieren, die im Rahmen eines Projektupgrades erfolgen muss. Diese Schnittstelle wird nicht aufgerufen, von <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, jedoch wird angegeben, wie möglicherweise nicht direkt über ein Mechanismus, um Dateien zu aktualisieren, die das Projektsystem, sondern dass das Hauptprojekt System gehören. Diese Situation kann beispielsweise eintreten, wenn die compilerbezogenen Dateien und Eigenschaften nicht vom gleichen Entwicklungsteam wie der Rest des Projektsystems betreut werden.  
  
### <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade-Implementierung  
 Wenn Ihr Projektsystem implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> es kann nur nicht Teil der **Visual Studio-Konvertierungs-Assistenten**. Allerdings auch, wenn Sie implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> -Schnittstelle, können Sie weiterhin den dateiupgrade zu delegieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Implementierung.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>So implementieren Sie IVsProjectUpgrade  
  
1.  Wenn ein Benutzer versucht, ein Projekt zu öffnen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Methode wird von der Umgebung aufgerufen, nachdem das Projekt geöffnet wurde und bevor andere Aktion für das Projekt ausgeführt werden kann. Wenn der Benutzer bereits aufgefordert wurde, aktualisieren Sie die Projektmappe, und klicken Sie dann die <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> Flag übergeben der `grfUpgradeFlags` Parameter. Wenn der Benutzer ein Projekt direkt, solche öffnet wie mithilfe der **vorhandenes Projekt hinzufügen** Befehl ein, und dann die <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> Flag nicht übergeben, und das Projekt muss der Benutzer zum upgrade auffordern.  
  
2.  Als Antwort auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> -Aufruf, ob die Projektdatei aktualisiert wird, muss das Projekt bewerten. Wenn das Projekt muss nicht den Projekttyp auf eine neue Version zu aktualisieren, können Sie einfach Zurückgeben der <xref:Microsoft.VisualStudio.VSConstants.S_OK> Flag.  
  
3.  Wenn das Projekt muss den Typ für Projekte auf eine neue Version zu aktualisieren, muss Sie ermitteln, ob die Projektdatei kann, durch Aufrufen geändert werden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> -Methode und übergeben des Werts der <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> für die `rgfQueryEdit` Parameter. In diesem Fall muss das Projekt folgendes ausführen:  
  
    -   Wenn die `VSQueryEditResult` zurückgegebene Wert in der `pfEditCanceled` Parameter ist <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>, und klicken Sie dann das Upgrade fortgesetzt werden kann, weil die Projektdatei geschrieben werden kann.  
  
    -   Wenn die `VSQueryEditResult` zurückgegebene Wert in der `pfEditCanceled` Parameter ist <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> und die `VSQueryEditResult` Wert hat die <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> -Bit festgelegt ist, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> muss einen Fehler zurückgeben, da der Benutzer das Berechtigungsproblem selbst aufgelöst werden soll. Das Projekt sollte dann Folgendes ausführen:  
  
         Melden Sie den Fehler an den Benutzer durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> und Zurückgeben der <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> Fehlercode <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
    -   Wenn die `VSQueryEditResult` Wert <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> und die `VSQueryEditResultFlags` Wert hat die <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> -Bit festgelegt ist, und klicken Sie dann die Projektdatei durch Aufrufen von ausgecheckt werden <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>,...).  
  
4.  Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> Aufruf auf die Projektdatei bewirkt, dass die Datei ausgecheckt werden, und die neueste Version abgerufen werden sollen, und klicken Sie dann das Projekt entladen und erneut geladen wird. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> -Methode erneut aufgerufen, nachdem eine andere Instanz des Projekts erstellt wird. Bei diesem zweiten Aufruf kann die Projektdatei auf den Datenträger geschrieben werden; es wird empfohlen, dass das Projekt eine Kopie der Projektdatei im vorherigen Format mit einer OLD-Erweiterung speichert, die für das Upgrade erforderlichen Änderungen vornimmt und die Projektdatei anschließend im neuen Format speichert. Erneut, wenn Sie einen beliebigen Teil des Upgradevorgangs ein Fehler auftritt, die Methode muss geben Fehler durch Zurückgeben von <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>. Dadurch wird das Projekt aus dem Projektmappen-Explorer entladen.  
  
     Es ist wichtig, den gesamten Prozess zu verstehen, die in der Umgebung für den Fall, in dem tritt auf, der Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> Methodenrückgabe (dabei den Wert "reportonly") der <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> und die <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> Flags.  
  
5.  Der Benutzer versucht, die Projektdatei zu öffnen.  
  
6.  Die Umgebung ruft Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> Implementierung.  
  
7.  Wenn <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> gibt `true`, und klicken Sie dann die Umgebung ruft Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> Implementierung.  
  
8.  Die Umgebung ruft Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> Implementierung so öffnen Sie die Datei, und initialisieren Sie das Projektobjekt, z. B. Projekt1.  
  
9. Die Umgebung ruft Ihre `IVsProjectUpgrade::UpgradeProject` -Implementierung auf, um zu bestimmen, ob ein Upgrade der Projektdatei erforderlich ist.  
  
10. Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> und übergeben den Wert der <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> für die `rgfQueryEdit` Parameter.  
  
11. Gibt die Umgebung <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> für `VSQueryEditResult` und <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> -Bit im `VSQueryEditResultFlags`.  
  
12. Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Standardimplementierung ruft `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>).  
  
 Dieser Aufruf kann dazu führen, dass eine neue Kopie Ihrer Projektdatei ausgecheckt und die neueste Version abgerufen wird, wodurch es erforderlich wird, die Projektdatei neu zu laden. An diesem Punkt geschieht eins von zwei Dingen:  
  
-   Wenn Sie eine eigene Laden des Projekts selbst behandelt, klicken Sie dann die Umgebung ruft Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> -Implementierung (VSITEMID_ROOT). Wenn Sie diesen Aufruf empfangen, laden Sie die erste Instanz des Projekts (Projekt1) erneut, und fahren Sie mit dem Upgrade Ihrer Projektdatei fort. Die Umgebung weiß, dass eigene Laden des Projekts behandeln, wenn Sie zurückkehren, `true` für <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>).  
  
-   Wenn Sie eigene Laden des Projekts nicht behandelt, Sie zurückkehren `false` für <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>). In diesem Fall vor dem <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) zurückgibt, erstellt die Umgebung eine andere neue Instanz des Projekts, z. B. "Projekt2", wie folgt:  
  
    1.  Die Umgebung ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> auf Ihr erstes Projektobjekt Projekt1, platzieren Sie daher dieses Objekts in den inaktiven Zustand.  
  
    2.  Die Umgebung ruft Ihre `IVsProjectFactory::CreateProject` -Implementierung auf, um eine zweite Instanz Ihres Projekts zu erstellen, „Project2“.  
  
    3.  Die Umgebung ruft Ihre `IPersistFileFormat::Load` -Implementierung auf, um die Datei zu öffnen und das zweite Projektobjekt, „Projekt2“, zu initialisieren.  
  
    4.  Die Umgebung ruft `IVsProjectUpgrade::UpgradeProject` ein zweites Mal auf, um zu bestimmen, ob für das Projektobjekt ein Upgrade ausgeführt werden soll. Dieser Aufruf erfolgt jedoch für eine neue, zweite Instanz des Projekts, „Projekt2“. Dies ist das Projekt, das in der Projektmappe geöffnet ist.  
  
        > [!NOTE]
        >  In der Instanz, die Ihrem erste Projekt Projekt1, befindet sich im Status "inaktiv" Sie müssen zurückgeben <xref:Microsoft.VisualStudio.VSConstants.S_OK> aus dem ersten Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Implementierung.  
  
    5.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> und übergeben den Wert der <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> für die `rgfQueryEdit` Parameter.  
  
    6.  Gibt die Umgebung <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> und das Upgrade kann fortgesetzt werden, weil die Projektdatei geschrieben werden kann.  
  
 Wenn Sie das upgrade versäumen, zurück <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> aus `IVsProjectUpgrade::UpgradeProject`. Wenn für Sie kein Upgrade erforderlich ist oder Sie sich gegen das Upgrade entscheiden, behandeln Sie den `IVsProjectUpgrade::UpgradeProject` -Aufruf als nicht erfolgten Vorgang (No-Op). Wenn Sie zurückkehren, <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>, die Projektmappe für das Projekt ein Platzhalterknoten hinzugefügt wird.  
  
## <a name="upgrading-project-items"></a>Aktualisieren von Projektelementen
  
Wenn Sie hinzufügen oder Verwalten von Elementen innerhalb von Projektsystemen, die Sie nicht implementieren, müssen Sie möglicherweise zur Teilnahme an des Projekt-Upgrade-Prozess. Crystal Reports ist ein Beispiel für ein Element, das mit dem Projektsystem hinzugefügt werden kann.  
  
 In der Regel Implementierer der Project-Element einem Projekt bereits vollständig instanziiert und aktualisierten nutzen möchten, da sie wissen, welche die Projekt-Verweise sind und was andere Projekteigenschaften vorhanden sind, um ein Upgrade Entscheidung zu treffen müssen.  
  
### <a name="to-get-the-project-upgrade-notification"></a>Zum Abrufen der Projekt-Upgrade-benachrichtigungs  
  
1.  Legen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> Flag (definiert in vsshell80.idl) in Ihrer Implementierung der Project-Element. Dies bewirkt, dass Ihr Projektelement VSPackage automatisch geladen, wenn die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell feststellt, dass ein Projektsystem ein Upgrade durchführen.  
  
2.  Empfehlen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> -Oberfläche über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> Methode.  
  
3.  Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> Schnittstelle wird ausgelöst, sobald die Projekt-System-Implementierung seiner upgradevorgänge abgeschlossen hat und die neue aktualisierte Projekt wird erstellt. Abhängig vom jeweiligen Szenario die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> Schnittstelle wird ausgelöst, nachdem die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, oder die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> Methoden.  
  
### <a name="to-upgrade-the-project-item-files"></a>So aktualisieren Sie die Projektdateien-Element  
  
1.  Sie müssen sorgfältig im Rahmen des Sicherungsvorgangs Datei in Ihrem Projekt Implementierung verwalten. Dies gilt insbesondere für eine Seite-an-Seite-Sicherung, in dem die `fUpgradeFlag` Parameter von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Methode auf festgelegt ist <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>, in der Dateien, die gesichert wurden entlang clientseitige Dateien platziert werden, die als ".old" gekennzeichnet sind. Die gesicherten Dateien, die älter sind als die Systemzeit, wenn das Projekt aktualisiert wurde, können als veraltet festgelegt werden. Darüber hinaus können sie überschrieben werden, es sei denn, um dies zu verhindern, dass bestimmte Schritte Unternehmen.  
  
2.  Zum Zeitpunkt des Projektelements eine Benachrichtigung über das Projektupgrade Ruft die **Visual Studio-Konvertierungs-Assistenten** wird weiterhin angezeigt. Daher sollten Sie die Methoden der verwenden die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> Schnittstelle, um das Upgrade Nachrichten für die Assistenten-Benutzeroberfläche bereitzustellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Projekte](../../extensibility/internals/projects.md)   
