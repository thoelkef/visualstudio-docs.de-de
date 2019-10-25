---
title: Projekt Konfiguration für Ausgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b6337d82e51cf728d69f7aabb46e9d4444ec564
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725883"
---
# <a name="project-configuration-for-output"></a>Projektkonfiguration für die Ausgabe
Jede Konfiguration kann einen Satz von Buildprozessen unterstützen, die Ausgabe Elemente wie z. b. ausführbare Dateien oder Ressourcen Dateien erstellen. Diese Ausgabe Elemente sind für den Benutzer Privat und können in Gruppen platziert werden, die Verwandte Ausgabetypen wie ausführbare Dateien (exe-, dll-, lib-) und Quelldateien (IDL-und h-Dateien) verknüpfen.

 Ausgabe Elemente können über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2>-Methoden zur Verfügung gestellt und mit den <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>-Methoden aufgelistet werden. Wenn Sie Ausgabe Elemente gruppieren möchten, sollte Ihr Projekt auch die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>-Schnittstelle implementieren.

 Das-Konstrukt, das durch Implementieren von `IVsOutputGroup` entwickelt wird, ermöglicht Projekten, Ausgaben entsprechend der Verwendung zu gruppieren. Beispielsweise kann eine DLL mit ihrer Programmdatenbank (PDB) gruppiert werden.

> [!NOTE]
> Eine PDB-Datei enthält Debuginformationen und wird erstellt, wenn beim Erstellen der DLL-oder exe-Datei die Option "Debuginformationen generieren" angegeben wird. Die PDB-Datei wird in der Regel nur für die debugprojektkonfiguration generiert.

 Das Projekt muss die gleiche Anzahl von Gruppen für jede unterstützte Konfiguration zurückgeben, obwohl die Anzahl der in einer Gruppe enthaltenen Ausgaben von der Konfiguration bis zur Konfiguration abweichen kann. Beispielsweise kann die DLL-Datei des Projekts mattd. dll und mattd. pdb in die Debugkonfiguration einschließen, aber nur Matt. dll in der Einzelhandels Konfiguration enthalten.

 Die Gruppen verfügen auch über die gleichen Bezeichnerinformationen, z. b. Kanonischer Name, Anzeige Name und Gruppeninformationen, von der Konfiguration bis zur Konfiguration innerhalb eines Projekts. Diese Konsistenz ermöglicht die Bereitstellung und Paket Erstellung, auch wenn sich die Konfigurationen ändern.

 Gruppen können auch eine Schlüsselausgabe aufweisen, die das Verpacken von Verknüpfungen ermöglicht, um auf etwas Sinnvolles zu zeigen. Jede Gruppe ist in einer bestimmten Konfiguration möglicherweise leer, sodass keine Annahmen über die Größe einer Gruppe erfolgen sollten. Die Größe (Anzahl der Ausgaben) der einzelnen Gruppen in einer beliebigen Konfiguration kann sich von der Größe einer anderen Gruppe in der gleichen Konfiguration unterscheiden. Sie kann sich auch von der Größe derselben Gruppe in einer anderen Konfiguration unterscheiden.

 ![Grafik zu Ausgabe Gruppen](../../extensibility/internals/media/vsoutputgroups.gif "vsoutputgroups") Ausgabe Gruppen

 Der primäre Einsatz der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> Schnittstelle ist die Bereitstellung des Zugriffs zum Erstellen, bereitstellen und Debuggen von Verwaltungs Objekten und ermöglicht es Projekten, Ausgaben zu gruppieren. Weitere Informationen zur Verwendung dieser Schnittstelle finden Sie unter [Project Configuration Object](../../extensibility/internals/project-configuration-object.md).

 Im vorherigen Diagramm hat eine Gruppe erstellt eine Schlüsselausgabe über Konfigurationen hinweg (entweder "BD. exe" oder "b. exe"), sodass der Benutzer eine Verknüpfung erstellen kann, die erstellt wird und weiß, dass die Verknüpfung unabhängig von der bereitgestellten Konfiguration funktioniert. Die Gruppen Quelle weist keine Schlüsselausgabe auf, sodass der Benutzer keine Verknüpfung damit erstellen kann. Wenn die integrierte debuggruppe über eine Schlüsselausgabe verfügt, die von der Einzelhandelsgruppe jedoch nicht erstellt wurde, wäre dies eine falsche Implementierung. Danach folgt Folgendes: Wenn eine Konfiguration eine Gruppe enthält, die keine Ausgaben enthält, und folglich keine Schlüsseldatei, können andere Konfigurationen mit dieser Gruppe, die Ausgaben enthalten, keine Schlüsseldateien haben. Die Installer-Editoren nehmen an, dass kanonische Namen und anzeigen Amen von Gruppen sowie das vorhanden sein einer Schlüsseldatei nicht auf der Grundlage von Konfigurationen geändert werden.

 Beachten Sie, dass die Ausgabe nicht in eine Gruppe eingefügt werden muss, wenn ein Projekt über eine `IVsOutputGroup` verfügt, die nicht Verpacken oder bereitgestellt werden soll. Die Ausgabe kann weiterhin normal aufgezählt werden, indem die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A>-Methode implementiert wird, die unabhängig von der Gruppierung alle Ausgaben der Konfiguration zurückgibt.

 Weitere Informationen finden Sie in der Implementierung von `IVsOutputGroup` im Beispiel für ein benutzerdefiniertes Projekt unter [MPF for Projects](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="see-also"></a>Siehe auch
- [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)
- [Projektkonfiguration beim Erstellen](../../extensibility/internals/project-configuration-for-building.md)
- [Projektkonfigurationsobjekt](../../extensibility/internals/project-configuration-object.md)
- [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md)