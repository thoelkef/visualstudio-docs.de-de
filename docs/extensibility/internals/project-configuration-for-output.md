---
title: Projektkonfiguration für Ausgabe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78b95457af4c5d806fdfcc20f49ac4e82df36488
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706672"
---
# <a name="project-configuration-for-output"></a>Projektkonfiguration für die Ausgabe
Jede Konfiguration kann eine Reihe von Buildprozessen unterstützen, die Ausgabeelemente wie ausführbare Dateien oder Ressourcendateien erzeugen. Diese Ausgabeelemente sind für den Benutzer privat und können in Gruppen platziert werden, die verwandte Ausgabetypen wie ausführbare Dateien (.exe, .dll, .lib) und Quelldateien (.idl, .h-Dateien) verknüpfen.

 Ausgabeelemente können über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> Methoden zur Verfügung gestellt <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> und mit den Methoden aufgezählt werden. Wenn Sie Ausgabeelemente gruppieren möchten, sollte <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> das Projekt auch die Schnittstelle implementieren.

 Das durch die `IVsOutputGroup` Implementierung entwickelte Konstrukt ermöglicht es Projekten, Ausgaben nach Verwendung zu gruppieren. Beispielsweise kann eine DLL mit ihrer Programmdatenbank (PDB) gruppiert werden.

> [!NOTE]
> Eine PDB-Datei enthält Debuginformationen und wird erstellt, wenn beim Erstellen der .dll oder EXe die Option "Debug-Informationen generieren" angegeben wird. Die .pdb-Datei wird normalerweise nur für die Debugprojektkonfiguration generiert.

 Das Projekt muss für jede unterstützte Konfiguration die gleiche Anzahl von Gruppen zurückgeben, auch wenn die Anzahl der in einer Gruppe enthaltenen Ausgaben von Konfiguration zu Konfiguration variieren kann. Die DLL des Projekts Matt kann z. B. mattd.dll und mattd.pdb in der Debugkonfiguration enthalten, aber nur matt.dll in der Retail-Konfiguration.

 Die Gruppen verfügen auch über dieselben Bezeichnerinformationen, z. B. kanonischen Namen, Anzeigename und Gruppeninformationen, von der Konfiguration bis zur Konfiguration innerhalb eines Projekts. Diese Konsistenz ermöglicht es, dass Die Bereitstellung und Verpackung auch dann weiter funktioniert, wenn sich die Konfigurationen ändern.

 Gruppen können auch über eine Schlüsselausgabe verfügen, mit der Verpackungsverknüpfungen auf etwas Sinnvolles verweisen können. Jede Gruppe ist in einer bestimmten Konfiguration möglicherweise leer, daher sollten keine Annahmen über die Größe einer Gruppe getroffen werden. Die Größe (Anzahl der Ausgaben) jeder Gruppe in jeder Konfiguration kann sich von der Größe einer anderen Gruppe in derselben Konfiguration unterscheiden. Sie kann sich auch von der Größe derselben Gruppe in einer anderen Konfiguration unterscheiden.

 ![Grafik "Ausgabegruppen"](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups") Ausgabegruppen

 Die primäre Verwendung <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> der Schnittstelle besteht darin, Zugriff auf Erstellen, Bereitstellen und Debuggen von Verwaltungsobjekten zu gewähren und Projekten die Freiheit zu geben, Ausgaben zu gruppieren. Weitere Informationen zur Verwendung dieser Schnittstelle finden Sie unter [Projektkonfigurationsobjekt](../../extensibility/internals/project-configuration-object.md).

 Im vorherigen Diagramm verfügt Group Built über eine Schlüsselausgabe über Konfigurationen (entweder bD.exe oder b.exe), sodass der Benutzer eine Verknüpfung zu Built erstellen und wissen kann, dass die Verknüpfung unabhängig von der bereitgestellten Konfiguration funktioniert. Gruppenquelle verfügt nicht über eine Schlüsselausgabe, sodass der Benutzer keine Verknüpfung dazu erstellen kann. Wenn die Debuggruppe Built über eine Schlüsselausgabe verfügt, die Retail Group Built jedoch nicht, wäre dies eine falsche Implementierung. Daraus folgt, dass, wenn eine Konfiguration über eine Gruppe verfügt, die keine Ausgaben enthält, und daher keine Schlüsseldatei, andere Konfigurationen mit dieser Gruppe, die Ausgaben enthalten, keine Schlüsseldateien haben können. Die Installer-Editoren gehen davon aus, dass sich kanonische Namen und Anzeigenamen von Gruppen sowie das Vorhandensein einer Schlüsseldatei nicht basierend auf Konfigurationen ändern.

 Beachten Sie, dass `IVsOutputGroup` es ausreicht, diese Ausgabe nicht in einer Gruppe zu setzen, wenn ein Projekt nicht verpackt oder bereitgestellt werden soll. Die Ausgabe kann weiterhin normal aufgezählt <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> werden, indem die Methode implementiert wird, die alle Ausgaben einer Konfiguration unabhängig von der Gruppierung zurückgibt.

 Weitere Informationen finden Sie `IVsOutputGroup` in der Implementierung von im Beispiel für benutzerdefinierte Projekte unter [MPF for Projects](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="see-also"></a>Weitere Informationen
- [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)
- [Projektkonfiguration beim Erstellen](../../extensibility/internals/project-configuration-for-building.md)
- [Projektkonfigurationsobjekt](../../extensibility/internals/project-configuration-object.md)
- [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md)
