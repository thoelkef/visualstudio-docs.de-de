---
title: Projektkonfiguration für die Ausgabe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d9bb68812ed9988c9ed18174231ead24f91fcf9d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132194"
---
# <a name="project-configuration-for-output"></a>Konfiguration für die Ausgabe des Projekts
Jede Konfiguration kann es sich um einen Satz von Erstellungsvorgängen unterstützen, die Ausgabeelemente z. B. ausführbare Datei oder Ressource Dateien zu erzeugen. Diese Ausgabeelemente, die dem Benutzer privat sind und in Gruppen, die verknüpft sind verwandte Typen in der Ausgabe z. B. ausführbare Dateien (.exe, DLL, .lib) und Quelldateien (IDL, h-Dateien) platziert werden können.  
  
 Ausgabeelemente durch verfügbar gemacht werden die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> Methoden und aufgezählten mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> Methoden. Wenn Sie Ausgabe gruppieren möchten, sollten auch das Projekt implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> Schnittstelle.  
  
 Das Konstrukt entwickelt, durch die Implementierung `IVsOutputGroup` können Projekte auf Gruppe Ausgaben gemäß Verwendung. Beispielsweise kann eine DLL mit der Programmdatenbank (PDB) gruppiert werden.  
  
> [!NOTE]
>  Eine PDB-Datei enthält Debuginformationen, und er wird erstellt, wenn "Debuginfo generieren"-Option angegeben wird, wenn Sie die .dll oder .exe erstellen. Die PDB-Datei wird in der Regel für Debug-Projektkonfiguration generiert.  
  
 Das Projekt muss die gleiche Anzahl von Gruppen für jede Konfiguration, die unterstützt wird, zurückgeben, obwohl die Anzahl von Ausgaben in einer Gruppe enthaltene aus Konfiguration variieren kann. Z. B. des Projekts Matt DLL möglicherweise enthalten mattd.dll und mattd.pdb in Debug-Konfiguration, jedoch nur matt.dll in Retail-Konfiguration.  
  
 Die Gruppen haben auch die gleichen Bezeichnerinformationen, z. B. kanonischen Namen und Anzeigenamen Gruppeninformationen, von Konfiguration innerhalb eines Projekts. Diese Konsistenz ermöglicht die Bereitstellung und paketerstellung für zwar weiterhin ausgeführt, selbst wenn die Konfiguration geändert werden.  
  
 Gruppen können auch eine wichtige Ausgabe aufweisen, mit dem Verpacken Verknüpfungen in einen aussagekräftigeren Namen verweisen können. Eine beliebige Gruppe kann in einer bestimmten Konfiguration leer sein, damit keine Annahmen über die Größe einer Gruppe erfolgen soll. Die Größe aller Gruppen in jeder Konfiguration (Anzahl von Ausgaben) kann sich von der Größe einer anderen Gruppe in der gleichen Konfiguration unterscheiden. Sie können auch von der Größe der gleichen Gruppe in eine andere Konfiguration sich unterscheiden.  
  
 ![Grafik zu Ausgabegruppen "Ausgabe"](../../extensibility/internals/media/vsoutputgroups.gif "VsOutputGroups")  
Ausgabegruppen  
  
 Der primäre Verwendungszweck der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> ist, ermöglichen den Zugriff zum Erstellen, bereitstellen und Debuggen von Verwaltungsobjekten und-Projekten die Freiheit gibt, Gruppe Ausgaben können-Schnittstelle. Weitere Informationen zur Verwendung dieser Schnittstelle finden Sie unter [Projekt Konfigurationsobjekt](../../extensibility/internals/project-configuration-object.md).  
  
 In der vorherigen Abbildung Gruppe erstellt, verfügt über einen Schlüssel, die Ausgabe über Konfigurationen (bD.exe oder b.exe), also der Benutzer kann erstellen Sie eine Verknüpfung, um integrierte und wissen, dass die Verknüpfung, unabhängig von der Konfiguration bereitgestellt funktioniert. Gruppe Quelle einen Schlüssel, der ausgegeben wird, keinen, damit der Benutzer eine Verknüpfung erstellen kann. Wenn weist eine wichtige Ausgabe auf der Debug-Gruppe erstellt, aber nicht die Retail-Gruppe erstellt, wäre, die eine falsche-Implementierung. Daraus folgt, klicken Sie dann, wenn eine Konfiguration, die keine Ausgaben, enthält eine Gruppe verfügt über, und daher keine Schlüsseldatei, und klicken Sie dann auf andere Konfigurationen mit dieser Gruppe, die Ausgaben enthalten keine Schlüsseldateien. Der Installer Editoren vorausgesetzt, dass die kanonischen Namen und Anzeigenamen von Gruppen sowie das Vorhandensein einer Schlüsseldatei nicht ändern basiert auf Konfigurationen.  
  
 Beachten Sie, dass, wenn ein Projekt enthält eine `IVsOutputGroup` , dass er nicht möchte Verpacken oder bereitstellen, ist es ausreichend, diese Ausgabe in einer Gruppe nicht eingefügt werden soll. Die Ausgabe immer noch aufgelistet werden kann, normalerweise durch die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> Methode, die alle von einer Konfiguration von Ausgaben unabhängig von der Gruppierung zurückgibt.  
  
 Weitere Informationen finden Sie auf die Implementierung der `IVsOutputGroup` in dem Beispiel von benutzerdefinierten Projekt-in [MPF für Projekte](http://mpfproj12.codeplex.com).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)   
 [Konfiguration für die Erstellung des Projekts](../../extensibility/internals/project-configuration-for-building.md)   
 [Projekt-Konfigurationsobjekt](../../extensibility/internals/project-configuration-object.md)   
 [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md)