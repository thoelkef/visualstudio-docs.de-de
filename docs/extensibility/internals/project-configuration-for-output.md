---
title: "Konfiguration f&#252;r die Ausgabe des Projekts | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projektkonfigurationen, Ausgabe"
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Konfiguration f&#252;r die Ausgabe des Projekts
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Jede Konfiguration kann es sich um einen Satz von Buildprozesse unterstützen, die Ausgabeelemente, z. B. ausführbare Datei oder Ressource zu erstellen. Diese Ausgabeelemente sind privat für den Benutzer und Gruppen, die verwandte Typen der Ausgabe z. B. ausführbare Dateien \(.exe, .dll, .lib\) und Quelldateien \(IDL, h\-Dateien\) verknüpft platziert werden können.  
  
 Ausgabeelemente durch verfügbar gemacht werden die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> Methoden und aufgelisteten mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> Methoden. Wenn Sie eine Ausgabe gruppieren möchten, muss ebenfalls das Projekt implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> Schnittstelle.  
  
 Das Konstrukt entwickelt, durch die Implementierung `IVsOutputGroup` können Projekte Gruppe Ausgaben gemäß Verwendung. Beispielsweise kann eine DLL mit der Programmdatenbank \(PDB\) gruppiert werden.  
  
> [!NOTE]
>  Eine PDB\-Datei Debuginformationen enthält, und erstellt, wenn "Debuginfo generieren"\-Option angegeben wird, wenn Sie die .dll oder .exe erstellen. Die PDB\-Datei wird in der Regel für die Debug\-Projektkonfiguration generiert.  
  
 Das Projekt muss die gleiche Anzahl von Gruppen für jede Konfiguration, die unterstützt wird, zurückgeben, obwohl die Anzahl von Ausgaben in einer Gruppe enthaltene aus Konfiguration variieren. Z. B. des Projekts Matt DLL möglicherweise einschließen mattd.dll und mattd.pdb in der Debugkonfiguration, jedoch nur matt.dll in Retail\-Konfiguration.  
  
 Die Gruppen haben auch die gleichen Informationen zur Identifizierung, wie kanonische Name, Anzeigename und Informationen, aus Konfiguration in einem Projekt. Diese Konsistenz ermöglicht die Bereitstellung und funktioniert auch bei Konfigurationen fortfahren.  
  
 Gruppen können auch eine wichtige Ausgabe aufweisen, mit der Verpackung Tastenkombinationen in einen aussagekräftigeren Namen verweisen können. Jede Gruppe kann in einer bestimmten Konfiguration leer sein, also keine Annahmen über die Größe einer Gruppe vorgenommen werden soll. Die Größe \(Anzahl der Ausgaben\) jeder Gruppe in einer Konfiguration kann von der Größe einer anderen Gruppe in der gleichen Konfiguration sein. Es kann auch von der Größe der gleichen Gruppe in eine andere Konfiguration unterschiedlich sein.  
  
 ![Grafik zu Ausgabegruppen](../../extensibility/internals/media/vsoutputgroups.png "vsOutputGroups")  
Ausgabegruppen  
  
 Der primäre Verwendungszweck der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> Schnittstelle wird zum Bereitstellen von Zugriff zum Erstellen, bereitstellen und Debuggen von Verwaltungsobjekten und\-Projekten die Freiheit, Gruppe Ausgaben können. Weitere Informationen zur Verwendung dieser Schnittstelle finden Sie unter [Projekt\-Konfigurationsobjekt](../../extensibility/internals/project-configuration-object.md).  
  
 Im vorherigen Diagramm Gruppe erstellt, verfügt über einen Schlüssel, die Ausgabe über Konfigurationen \(bD.exe oder b.exe\), also der Benutzer wissen, dass die Verknüpfung unabhängig von der Konfiguration bereitgestellt funktioniert und erstellen Sie eine Verknüpfung mit integrierten kann. Gruppe Quelle einen Schlüssel für die Ausgabe keinen daher der Benutzer eine Verknüpfung erstellen. Wenn eine wichtige Ausgabe der Debug\-Gruppe erstellt wurde, jedoch nicht die Retail\-Gruppe erstellt, wäre, die einer falschen Implementierung. Daraus folgt, dann verfügt jede Konfiguration eine Gruppe, die keine Ausgaben enthält, und daher keine Schlüsseldatei, und klicken Sie dann auf andere Konfigurationen mit dieser Gruppe, die Ausgaben enthalten keine Dateien. Die Installer\-Editoren davon ausgehen, dass kanonischen Namen und Anzeigenamen von Gruppen sowie das Vorhandensein einer Schlüsseldatei nicht ändern basiert auf Konfigurationen.  
  
 Beachten Sie, dass, wenn ein Projekt enthält eine `IVsOutputGroup` dass er nicht möchte, Verpacken oder bereitstellen, ist es ausreichend, diese Ausgabe nicht in einer Gruppe abgelegt. Die Ausgabe immer noch aufgelistet werden kann, normalerweise durch die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> \-Methode, die alle von einer Konfiguration Ausgaben unabhängig von der Gruppierung zurückgibt.  
  
 Weitere Informationen finden Sie in der Implementierung des `IVsOutputGroup` im Beispiel benutzerdefinierte Projekt am [MPF für Projekte](http://mpfproj12.codeplex.com).  
  
## Siehe auch  
 [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)   
 [Konfiguration zum Erstellen des Projekts](../../extensibility/internals/project-configuration-for-building.md)   
 [Projekt\-Konfigurationsobjekt](../../extensibility/internals/project-configuration-object.md)   
 [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md)