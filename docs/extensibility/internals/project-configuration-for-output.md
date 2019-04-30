---
title: Projektkonfiguration für die Ausgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7ac9c63a8524de17541a46f4fecb9e8d9a5ff69
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63423306"
---
# <a name="project-configuration-for-output"></a>Projektkonfiguration für die Ausgabe
Jeder Konfiguration kann es sich um einen Satz von Erstellungsvorgängen unterstützen, die Ausgabe-Elementen, z. B. ausführbare Datei oder Ressource Dateien zu erzeugen. Diese Ausgabeelemente sind für den Benutzer privat und platziert werden können, in Gruppen, die verwandte Typen, die Ausgabe, z. B. ausführbare Dateien (".exe", ".dll", ".lib") und Quelldateien (IDL, h-Dateien) zu verknüpfen.

 Ausgabeelemente können zur Verfügung gestellt durch die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> Methoden und aufgelisteten mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> Methoden. Wenn Sie die Ausgabe die Gruppenelemente möchten, sollten auch das Projekt implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> Schnittstelle.

 Das Konstrukt entwickelt, durch die Implementierung `IVsOutputGroup` können Projekte auf Gruppe Ausgaben entsprechend der Verwendung. Beispielsweise kann eine DLL-Datei mit der Programmdatenbank (PDB) gruppiert werden.

> [!NOTE]
> Eine PDB-Datei enthält Debuginformationen aus, und es erstellt, wenn die Option "Debuginfo generieren" angegeben wird, wenn Sie die .dll oder .exe erstellen. Die PDB-Datei wird in der Regel für Debug-Projektkonfiguration generiert.

 Das Projekt muss die gleiche Anzahl von Gruppen für jede Konfiguration, die dies unterstützen, zurückgeben, auch wenn die Anzahl von Ausgaben in einer Gruppe enthaltene Konfiguration auf Konfiguration variieren. Z. B. des Projekts Matt DLL möglicherweise mattd.dll und mattd.pdb in Debug-Konfiguration enthalten, jedoch nur matt.dll in Retail-Konfiguration.

 Die Gruppen haben auch die gleichen Bezeichnerinformationen, wie kanonische Name, Anzeigename und Gruppeninformationen, Konfiguration auf Konfiguration in einem Projekt. Diese Konsistenz ermöglicht die Bereitstellung und paketerstellung für weiterhin ausgeführt, auch wenn die Konfigurationen zu ändern.

 Gruppen können auch eine wichtige Ausgabe aufweisen, mit der paketerstellung Verknüpfungen in einen aussagekräftigeren Namen verweisen können. Eine beliebige Gruppe möglicherweise in einer bestimmten Konfiguration leer, damit keine Annahmen über die Größe einer Gruppe erfolgen soll. Die Größe (Anzahl von Ausgaben) der Gruppe "Jeder" in jeder Konfiguration kann von der Größe einer anderen Gruppe in der gleichen Konfiguration abweichen. Sie können auch von der Größe der gleichen Gruppe in einer anderen Konfiguration abweichen.

 ![Grafik zu Ausgabegruppen "Ausgabe"](../../extensibility/internals/media/vsoutputgroups.gif "VsOutputGroups") Ausgabegruppen

 Der primäre Verwendungszweck der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> ist, bieten Zugang zum Erstellen, bereitstellen und Debuggen von Verwaltungsobjekten und können Projekte die Freiheit gibt, die Ausgaben von Gruppe-Schnittstelle. Weitere Informationen zur Verwendung dieser Schnittstelle finden Sie unter [Projektkonfigurationsobjekt](../../extensibility/internals/project-configuration-object.md).

 Im vorherigen Diagramm Gruppe erstellt, verfügt über einen Schlüssel, die Ausgabe in Konfigurationen (bD.exe oder b.exe), daher kann der Benutzer erstellen Sie eine Verknüpfung, um integrierte und wissen, dass die Verknüpfung unabhängig von der Konfiguration bereitgestellt funktioniert. Gruppenquelle besitzt keinen Schlüssel für die Ausgabe, sodass der Benutzer eine Verknüpfung erstellen, kann nicht. Wenn die Debug-Gruppe erstellt eine wichtige Ausgabe wurde, aber nicht die Retail-Gruppe erstellt, wäre, die eine falsche Implementierung. Daraus folgt, dann verfügt jede Konfiguration eine Gruppe, die keine Ausgaben, enthält und daher keine Schlüsseldatei, und klicken Sie dann auf andere Konfigurationen, die diese Gruppe, die Ausgaben enthalten keine Dateien mit Schlüsseln. Die Installer-Editoren davon ausgehen, dass kanonischen Namen und Anzeigenamen von Gruppen sowie das Vorhandensein einer Schlüsseldatei ein, nicht ändern basiert auf Konfigurationen.

 Beachten Sie, dass, wenn ein Projekt enthält eine `IVsOutputGroup` , dass er nicht möchte, Verpacken oder bereitstellen, ist es ausreichend, platzieren Sie diese Ausgabe in einer Gruppe nicht. Die Ausgabe immer noch aufgelistet werden kann, normalerweise durch die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> Methode, die alle von einer Konfiguration der Ausgaben unabhängig von der Gruppierung zurückgibt.

 Weitere Informationen finden Sie auf die Implementierung der `IVsOutputGroup` in dem Beispiel von benutzerdefinierten Projekt-in [MPF für Projekte](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="see-also"></a>Siehe auch
- [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)
- [Projektkonfiguration beim Erstellen](../../extensibility/internals/project-configuration-for-building.md)
- [Projektkonfigurationsobjekt](../../extensibility/internals/project-configuration-object.md)
- [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md)