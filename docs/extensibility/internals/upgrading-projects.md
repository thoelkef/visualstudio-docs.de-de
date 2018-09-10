---
title: Aktualisieren von Projekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ea5c29819d0035e45f97122fd108ea1f51d60806
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057529"
---
# <a name="upgrading-projects"></a>Aktualisieren von Projekten

Änderungen an das Modell von einer Version von Visual Studio auf die nächste erfordern, dass Projekte und Projektmappen aktualisiert werden, sodass sie die neuere Version ausgeführt werden können. Die [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] enthält Schnittstellen, die zum Implementieren von Unterstützung in Ihren eigenen Projekten verwendet werden können.

## <a name="upgrade-strategies"></a>Aktualisierungsstrategien

Um ein Upgrade zu unterstützen, muss die Project-System-Implementierung definieren und implementieren eine Strategie für die Aktualisierung. Bei der Bestimmung Ihrer Strategie, können Sie auswählen, um Side-by-Side (SxS) Sicherung, Sicherung kopieren oder beides zu unterstützen.

-   Parallele Sicherung bedeutet, dass ein Projekt nur die Dateien kopiert, die ein Upgrade Direktes Hinzufügen einer geeigneten Dateinamensuffix, z. B. ".old".

-   Kopieren Sie die Sicherung bedeutet, dass ein Projekt alle Projektelemente in einen vom Benutzer bereitgestellte Sicherungsspeicherort kopiert. Die relevanten Dateien auf den Speicherort des ursprünglichen Projekts werden anschließend aktualisiert.

## <a name="how-upgrade-works"></a>Funktionsweise von Upgrades

Wenn eine Lösung, die in einer früheren Version von Visual Studio erstellt, die in einer neueren Version geöffnet wird, überprüft die IDE die Projektmappendatei, um festzustellen, ob sie ein Upgrade erforderlich ist. Wenn ein Upgrade erforderlich ist, ist die **Aktualisierungs-Assistenten** wird automatisch gestartet, um den Benutzer über den Upgradeprozess geführt.

Wenn eine Lösung aktualisieren benötigt, wird jedes Projekt-Factory für die Upgrade-Strategie abgefragt. Die Strategie bestimmt, ob die Projektzuordnungsinstanz kopieren oder SxS-Sicherung unterstützt. Die Informationen werden gesendet, um die **Aktualisierungs-Assistenten**, die für die Sicherung erforderliche Informationen erfasst und zeigt die zutreffenden Optionen für dem Benutzer.

### <a name="multi-project-solutions"></a>Projektmappen mit mehreren Projekten

Wenn eine Projektmappe mehrere Projekte enthält, und die Aktualisierungsstrategien unterscheiden, wie z. B. beim Erstellen eines C++-Projekts, das nur parallele Sicherung unterstützt und ein Webprojekt, die nur Sicherung kopieren unterstützt, die projektfactorys der Aktualisierungsstrategie aushandeln müssen.

Die Lösung Abfragen für jedes Projekt-Factory <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Es ruft dann <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> um festzustellen, ob die globale Projektdateien benötigen aktualisieren und die unterstützten Aktualisierungsstrategien zu ermitteln. Die **Aktualisierungs-Assistenten** wird dann aufgerufen.

Nach Abschluss des Assistenten, durch der Benutzer <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> für jedes Projekt-Factory zum Ausführen des tatsächlichen Upgrades aufgerufen wird. Um die Sicherung zu erleichtern, IVsProjectUpgradeViaFactory dienen der <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> Dienst, der die Details des Upgradeprozesses protokollieren. Dieser Dienst kann nicht zwischengespeichert werden.

Nach der Aktualisierung aller relevanten globale Dateien kann jedes Projekt-Factory zum Instanziieren ein Projekt auswählen. Die Projekt-Implementierung unterstützen muss <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Methode wird aufgerufen, um alle relevanten Projektelemente zu aktualisieren.

> [!NOTE]
> Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Methode der SVsUpgradeLogger-Dienst nicht bereitstellt. Dieser Dienst abgerufen werden kann, durch den Aufruf <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.

## <a name="best-practices"></a>Bewährte Methoden

Verwenden der <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> Dienst zu überprüfen, ob Sie eine Datei vor der Bearbeitung bearbeiten können, und vor dem Speichern speichern können. Dadurch wird die Sicherung und Upgrade Implementierungen verarbeiten, Projektdateien unter quellcodeverwaltung, Dateien mit nicht genügend Berechtigungen, und So weiter.

Verwenden der <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> service in allen Phasen der Sicherung und upgrade, um Informationen zu den Erfolg oder Misserfolg des Upgradevorgangs bereitzustellen.

Weitere Informationen zum Sichern und Aktualisieren von Projekten finden Sie unter die Kommentare für IVsProjectUpgrade in vsshell2.idl.

## <a name="upgrading-custom-projects"></a> Aktualisieren von benutzerdefinierten Projekten

Wenn Sie die in der Projektdatei dauerhaft gespeicherten Informationen zwischen verschiedenen Visual Studio-Versionen Ihres Produkts ändern, müssen Sie das Durchführen eines Upgrades der Projektdatei von der alten auf die neue Version unterstützen. Zur Unterstützung der aktualisieren, die Ihnen ermöglicht, die Teilnahme an der **Visual Studio-Konvertierungs-Assistenten**, implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Schnittstelle. Diese Schnittstelle stellt das einzige verfügbare Verfahren zum Durchführen von Kopierupgrades dar. Das Upgrade des Projekts erfolgt im Rahmen des Öffnens der Projektmappe. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Schnittstelle wird von der Projektfactory implementiert oder sollte zumindest sein, dass von der Projektfactory.

Der alte Mechanismus, der verwendet die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Benutzeroberfläche wird weiterhin unterstützt, aber im Prinzip das Upgrade des als Teil des Projekts öffnen. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Schnittstelle wird daher aufgerufen, der Visual Studio-Umgebung selbst dann durch die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Schnittstelle aufgerufen wird oder implementiert ist. Dieser Ansatz ermöglicht Ihnen die Verwendung <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> die Kopie zu implementieren und nur Teile des Upgrades zu projizieren und delegieren die restlichen Aufgaben für ein direktes (möglicherweise auf dem neuen Speicherort) ausgeführt werden, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Schnittstelle.

Eine beispielimplementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, finden Sie unter [VSSDK-Beispiele](http://aka.ms/vs2015sdksamples).

Im Rahmen von Projektupgrades stellen sich die folgenden Szenarien dar:

-   Wenn die Datei ein neueres Format aufweist, als es vom Projekt unterstützt werden kann, muss eine Fehlermeldung zurückgegeben werden, aus der dieser Umstand hervorgeht. Dies setzt voraus, dass die ältere Version Ihres Produkts zum Überprüfen der Version enthält.

-   Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> Flag angegeben wird, der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> -Methode, das Upgrade wird als ein direktes Upgrade vor dem Öffnen des Projekts implementiert werden.

-   Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> Flag angegeben wird, der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> -Methode, das Upgrade als kopierupgrade implementiert wird.

-   Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> Flag angegeben wird, der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> aufrufen, und klicken Sie dann der Benutzer von der Umgebung aufgefordert wurde, um ein upgrade der Projektdatei als ein direktes Upgrade, nachdem das Projekt geöffnet wird. Beispielsweise fordert die Umgebung den Benutzer zum Upgrade auf, wenn der Benutzer eine ältere Version der Lösung öffnet.

-   Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> Flag nicht angegeben wird, der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> aufrufen, und klicken Sie dann aufgefordert, den Benutzer zum upgrade der Projektdatei müssen.

     Die folgende Aufforderungsnachricht stellt ein Beispiel dar:

     "Das Projekt '%1' wurde in einer älteren Version von Visual Studio erstellt. Wenn Sie es mit dieser Version von Visual Studio öffnen, können Sie es möglicherweise nicht mehr mit älteren Versionen von Visual Studio öffnen. Möchten Sie fortfahren und dieses Projekt öffnen?"

### <a name="to-implement-ivsprojectupgradeviafactory"></a>So implementieren Sie IVsProjectUpgradeViaFactory

1.  Implementieren Sie die Methode von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Schnittstelle, insbesondere die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> -Methode in Ihrer projektfactoryimplementierung, oder machen Sie die Implementierungen von Ihrer projektfactoryimplementierung aufgerufen.

2.  Wenn Sie ein direktes Upgrade als Teil des Öffnens der Projektmappe tun möchten, geben Sie das Flag <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> als die `VSPUVF_FLAGS` Parameter in Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Implementierung.

3.  Wenn Sie ein direktes Upgrade als Teil des Öffnens der Projektmappe tun möchten, geben Sie das Flag <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> als die `VSPUVF_FLAGS` Parameter in Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Implementierung.

4.  Für die Schritte 2 und 3, die eigentlichen dateiupgradeschritte, mithilfe von <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, können implementiert werden, wie beschrieben in der "implementieren `IVsProjectUpgade`" weiter unten im Abschnitt, oder Sie können das eigentliche dateiupgrade zu delegieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

5.  Verwenden Sie die Methoden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> beziehen Sie Upgrade veröffentlichen Nachrichten für den Benutzer, die mit Visual Studio-Migrations-Assistenten.

6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> Schnittstelle wird verwendet, um jede Art von dateiupgrade zu implementieren, die im Rahmen eines Projektupgrades erfolgen muss. Diese Schnittstelle wird nicht aufgerufen, von <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, aber möglicherweise nicht direkt über ein Mechanismus, um Dateien zu aktualisieren, die das Projektsystem, aber das Hauptprojekt-System gehören angegeben ist. Diese Situation kann beispielsweise eintreten, wenn die compilerbezogenen Dateien und Eigenschaften nicht vom gleichen Entwicklungsteam wie der Rest des Projektsystems betreut werden.

### <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade-Implementierung

Wenn Ihr Projektsystem implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> es kann nur nicht teilnehmen die **Visual Studio-Konvertierungs-Assistenten**. Aber selbst wenn Sie implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> -Schnittstelle, Sie können weiterhin das dateiupgrade zu delegieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Implementierung.

#### <a name="to-implement-ivsprojectupgrade"></a>So implementieren Sie IVsProjectUpgrade

1.  Wenn ein Benutzer versucht, ein Projekt zu öffnen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Methode wird von der Umgebung aufgerufen, nachdem das Projekt geöffnet wurde und bevor andere Benutzeraktionen für das Projekt ausgeführt werden können. Wenn der Benutzer bereits aufgefordert wurde, aktualisieren Sie die Projektmappe, und klicken Sie dann die <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> Flag übergeben die `grfUpgradeFlags` Parameter. Wenn der Benutzer ein Projekt direkt, solche öffnet wie mit der **vorhandenes Projekt hinzufügen** Befehl ein, und klicken Sie dann die <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> Flag nicht übergeben, und das Projekt muss der Benutzer zum upgrade auffordern.

2.  Als Reaktion auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> -Aufruf, ob die Projektdatei aktualisiert wird, muss das Projekt bewerten. Wenn das Projekt muss nicht den Projekttyp auf eine neue Version zu aktualisieren, kann er einfach Zurückgeben der <xref:Microsoft.VisualStudio.VSConstants.S_OK> Flag.

3.  Wenn das Projekt muss den Projekttyp auf eine neue Version zu aktualisieren, muss Sie ermitteln, ob die Projektdatei kann, durch den Aufruf geändert werden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> -Methode und übergeben des Werts der <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> für die `rgfQueryEdit` Parameter. In diesem Fall muss das Projekt folgendes ausführen:

    -   Wenn die `VSQueryEditResult` zurückgegebene Wert in der `pfEditCanceled` Parameter <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>, und klicken Sie dann das Upgrade fortgesetzt werden kann, weil die Projektdatei geschrieben werden kann.

    -   Wenn die `VSQueryEditResult` zurückgegebene Wert in der `pfEditCanceled` -Parameter ist <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> und `VSQueryEditResult` Wert hat die <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> -Bit festgelegt ist, klicken Sie dann <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> muss einen Fehler zurückgeben, da der Benutzer das Berechtigungsproblem selbst lösen müssen. Das Projekt sollte dann Folgendes ausführen:

         Melden Sie den Fehler an den Benutzer durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> und Zurückgeben der <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> Fehlercode <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

    -   Wenn die `VSQueryEditResult` Wert <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> und `VSQueryEditResultFlags` Wert hat die <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> -Bit festgelegt ist, aus, und klicken Sie dann die Projektdatei durch Aufrufen von ausgecheckt werden <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>,...).

4.  Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> Aufruf auf die Projektdatei führt dazu, dass die Datei ausgecheckt werden, und die neueste Version abgerufen werden sollen, und klicken Sie dann das Projekt entladen und neu geladen wird. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> -Methode erneut aufgerufen, nachdem eine andere Instanz des Projekts erstellt wurde. Bei diesem zweiten Aufruf kann die Projektdatei auf den Datenträger geschrieben werden; es wird empfohlen, dass das Projekt eine Kopie der Projektdatei im vorherigen Format mit einer OLD-Erweiterung speichert, die für das Upgrade erforderlichen Änderungen vornimmt und die Projektdatei anschließend im neuen Format speichert. Erneut, wenn Sie einen beliebigen Teil des Upgradevorgangs ein Fehler auftritt, die Methode muss geben Fehler durch Zurückgeben von <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>. Dadurch wird das Projekt aus dem Projektmappen-Explorer entladen.

     Es ist wichtig, den vollständigen Prozess zu verstehen, die in der Umgebung für den Fall, in dem tritt auf, den Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> Methodenrückgabe (dabei den Wert "reportonly") der <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> und <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> Flags.

5.  Der Benutzer versucht, die Projektdatei zu öffnen.

6.  Die Umgebung ruft Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> Implementierung.

7.  Wenn <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> gibt `true`, und klicken Sie dann die Umgebung ruft Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> Implementierung.

8.  Die Umgebung ruft Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> Implementierung so öffnen Sie die Datei, und initialisieren Sie das Projektobjekt, z. B. Project1 ab.

9. Die Umgebung ruft Ihre `IVsProjectUpgrade::UpgradeProject` -Implementierung auf, um zu bestimmen, ob ein Upgrade der Projektdatei erforderlich ist.

10. Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> und übergeben Sie einen Wert von <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> für die `rgfQueryEdit` Parameter.

11. Gibt die Umgebung <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> für `VSQueryEditResult` und <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> Bit ist gesetzt, `VSQueryEditResultFlags`.

12. Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Standardimplementierung ruft `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>).

Dieser Aufruf kann dazu führen, dass eine neue Kopie Ihrer Projektdatei ausgecheckt und die neueste Version abgerufen wird, wodurch es erforderlich wird, die Projektdatei neu zu laden. An diesem Punkt geschieht eins von zwei Dingen:

-   Wenn Sie Ihre eigenen erneute Laden des Projekts behandelt, klicken Sie dann die Umgebung ruft Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> -Implementierung (VSITEMID_ROOT). Wenn Sie diesen Aufruf empfangen, laden Sie die erste Instanz des Projekts (Projekt1) erneut, und fahren Sie mit dem Upgrade Ihrer Projektdatei fort. Die Umgebung weiß, dass Sie Ihre eigenen erneute Laden des Projekts behandeln, wenn Sie zurückkehren `true` für <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>).

-   Wenn Sie zurückkehren, behandeln Sie keine eigene erneute Laden des Projekts `false` für <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>). In diesem Fall vor dem <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) zurückgegeben wird, Erstellen der Umgebung eine andere neue Instanz des Projekts, z. B. "Projekt2", wie folgt:

    1.  Die Umgebung ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> in Ihr erstes Projektobjekt Projekt1, platzieren Sie daher dieses Objekt in den inaktiven Status.

    2.  Die Umgebung ruft Ihre `IVsProjectFactory::CreateProject` -Implementierung auf, um eine zweite Instanz Ihres Projekts zu erstellen, „Project2“.

    3.  Die Umgebung ruft Ihre `IPersistFileFormat::Load` -Implementierung auf, um die Datei zu öffnen und das zweite Projektobjekt, „Projekt2“, zu initialisieren.

    4.  Die Umgebung ruft `IVsProjectUpgrade::UpgradeProject` ein zweites Mal auf, um zu bestimmen, ob für das Projektobjekt ein Upgrade ausgeführt werden soll. Dieser Aufruf erfolgt jedoch für eine neue, zweite Instanz des Projekts, „Projekt2“. Dies ist das Projekt, das in der Projektmappe geöffnet ist.

        > [!NOTE]
        > In der Instanz, die Ihr erste Projekt Project1 befindet sich in den inaktiven Status, und Sie müssen zurückgeben <xref:Microsoft.VisualStudio.VSConstants.S_OK> aus dem ersten Aufruf von Ihrem <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Implementierung.

    5.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> und übergeben Sie einen Wert von <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> für die `rgfQueryEdit` Parameter.

    6.  Gibt die Umgebung <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> und das Upgrade kann fortgesetzt werden, weil die Projektdatei geschrieben werden kann.

Wenn Sie nicht aktualisieren, zurück <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> aus `IVsProjectUpgrade::UpgradeProject`. Wenn für Sie kein Upgrade erforderlich ist oder Sie sich gegen das Upgrade entscheiden, behandeln Sie den `IVsProjectUpgrade::UpgradeProject` -Aufruf als nicht erfolgten Vorgang (No-Op). Wenn Sie zurückkehren <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>, mit der Lösung für Ihr Projekt ein Platzhalterknoten hinzugefügt.

## <a name="upgrading-project-items"></a>Aktualisieren von Projektelementen

Wenn Sie hinzufügen oder Verwalten von Elementen im Projektsystemen, die Sie nicht implementieren, müssen Sie möglicherweise zur Teilnahme an des Projekt-Upgrade-Prozess. Crystal Reports ist ein Beispiel für ein Element, das an das Projektsystem hinzugefügt werden kann.

In der Regel Implementierungen der Project-Element einem Projekt bereits vollständig instanziierte und aktualisierten nutzen möchten, weil sie wissen, welches die Projekt-Verweise sind und welche anderen Eigenschaften des Projekts vorhanden sind, um ein Upgrade Entscheidung zu treffen müssen.

### <a name="to-get-the-project-upgrade-notification"></a>Um die Projekt-Upgrade-Benachrichtigung zu erhalten.

1.  Legen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> Flag (definiert in der vsshell80.idl) in Ihrer Implementierung der Project-Element. Dies bewirkt, dass Ihr Projektelement VSPackage automatisch geladen, wenn die Visual Studio Shell feststellt, dass ein Projektsystem im Aktualisierungsprozess ist.

2.  Empfehlen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> -Oberfläche über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> Methode.

3.  Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> Schnittstelle wird immer dann ausgelöst, nachdem die systemimplementierung des Projekts ein Upgrade abgeschlossen wurde aus, und die neue, aktualisierte Projekt wird erstellt. Je nach Szenario das <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> Schnittstelle wird ausgelöst, nachdem die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, oder die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> Methoden.

### <a name="to-upgrade-the-project-item-files"></a>So aktualisieren die Element-Projektdateien

1.  Sie müssen sorgfältig den Sicherungsvorgang für die Datei in Ihrer Implementierung der Project-Element verwalten. Dies gilt insbesondere für eine Seite-an-Seite-Sicherung, in denen die `fUpgradeFlag` Parameter der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Methode nastaven NA hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>, in Dateien, die gesichert wurden auf der Seite Dateien platziert werden, die als ".old" gekennzeichnet sind. Die gesicherten Dateien, die älter sind als die Systemzeit, wenn das Projekt aktualisiert wurde, können als veraltet festgelegt werden. Darüber hinaus können sie überschrieben werden, es sei denn, Sie bestimmte Schritte, um dies zu verhindern, dass Unternehmen.

2.  Zum Zeitpunkt des Projektelements eine Benachrichtigung über das Upgraden von Projekten, ruft der **Visual Studio-Konvertierungs-Assistenten** wird weiterhin angezeigt. Aus diesem Grund sollten Sie die Methoden verwenden die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> Schnittstelle, um ein Upgrade von Nachrichten auf der Benutzeroberfläche des Assistenten bereitzustellen.

## <a name="see-also"></a>Siehe auch

- [Projekte](../../extensibility/internals/projects.md)