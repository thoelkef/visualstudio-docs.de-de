---
title: "-Bezogenen Diensten und Schnittstellen (Source Control VSPackage) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Quellcode-Verwaltungspaketen, Schnittstellen"
  - "Quellcode-Verwaltungspaketen-Schnittstellen"
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# -Bezogenen Diensten und Schnittstellen (Source Control VSPackage)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In diesem Abschnitt sind alle Quellcodeverwaltung VSPackage\-verknüpften Schnittstellen in [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]auf.  Die Quellcodeverwaltung VSPackage implementiert einige dieser Schnittstellen und Quellcodeverwaltung verwendet, um andere Aufgaben auszuführen.  
  
## Schnittstellen implementiert und von VSPackages für die Quellcodeverwaltung  
 Die folgenden Schnittstellen sind in [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]beschrieben, und die Quellcodeverwaltung ein VSPackage implementiert eine Teilmenge davon je nach gewünschten Funktionsumfang.  Einige Schnittstellen werden nach Bedarf gekennzeichnet und müssen von einer Quellcodeverwaltung VSPackage implementiert werden.  
  
 Für diese Schnittstellen, die ein Paket nicht implementiert, stellt eine Standardimplementierung [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Beachten Sie, dass die Standardimplementierung für den Fall entworfen wird, wenn kein VSPackage registriert ist und kein Projekts gesteuert wird.  Ein VSPackage Quellcodeverwaltung Schreibvorgang ordnungsgemäß implementiert alle erforderlichen Schnittstellen anstatt es der Standardimplementierung dieser Schnittstellen überlassend.  
  
 Eine Quellcodeverwaltung VSPackage muss einen privaten Dienst, der einige oder kapselt alle der folgenden Schnittstellen implementieren.  
  
 Schnittstellen sind:  
  
-   Erforderlich: Die entsprechende Entität \(Quellcodeverwaltung VSPackage, Quellcodeverwaltungs\-Stub Projekt\), muss die Schnittstelle implementieren.  
  
-   Empfohlen: Die Entität muss diese Schnittstelle implementieren. Andernfalls wird die Quellcodeverwaltung eingeschränkt werden.  
  
-   Optional: die Entität kann diese Schnittstelle implementieren, um einen umfangreicheren Funktionsumfang bereitzustellen.  
  
|Schnittstelle|Zweck|Vorbei implementiert|implementieren?|  
|-------------------|-----------|--------------------------|---------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Editoren rufen diese Schnittstelle auf, bevor sie eine Datei bearbeiten und speichern.  Die Quellcodeverwaltung kann ein VSPackage die Datei auschecken oder den Vorgang verweigern, wenn das Auschecken fehlschlägt.|Quellcodeverwaltung VSPackage|Empfohlen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Diese Schnittstelle stellt grundlegende Funktionen für Quellcodeverwaltung für Projekte wie Registrieren und Aufheben der Registrierung von Projekten mit Quellcodeverwaltung und Gewähren der Quellcodeverwaltung grundlegende Unterstützung für Symbole.|Quellcodeverwaltung VSPackage|Erforderlich|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Diese Schnittstelle wird von <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> mithilfe der <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>\-Funktion abgerufen oder indem Sie einfach das Objekt umwandeln, das `IVsHierarchy` zu `IVsSccProject2`implementiert.  Sie wird für den Abruf der Dateien in der Quellcodeverwaltung in einem Projekt oder zum Informieren des Projekts über den Status steuer aktuellen Quelle oder Speicherort verwendet.|Project|Erforderlich|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>|Das Modul Integrations verwendet diese Schnittstelle, um aktuelle aktive VSPackage festzulegen.|Quellcodeverwaltung VSPackage|Erforderlich|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Diese Schnittstelle basiert auf einem Abonnement Modells.  Jedes VSPackage kann signalisieren, dass er Dokumentereignisse empfangen und von der Shell für Ereignisse protokolliert werden sollen, die ausgeführt werden soll.  Er wird von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]implementiert und dazu verwendet, das wiederum die Ereignisse, die `IVsTrackProjectDocumentsEvents2` in einem VSPackage implementieren.|Quellcodeverwaltungs\-Stub|Erforderlich|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|Diese Schnittstelle stellt die Batchverarbeitung, synchronisierte Vorgänge mit Lese\-\/Schreibzugriff und eine erweiterte `OnQueryAddFiles`\-Methode.|Quellcodeverwaltungs\-Stub|Erforderlich|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|**Projektmappen\-Explorer** und Projekte rufen diese Schnittstelle auf, wenn neuer Dateien zu Projekten hinzugefügt werden oder wenn Dateien und Ordner aus Projekten umbenannt oder gelöscht werden.  Die Quellcodeverwaltung auschecken die Projektdatei kann ein VSPackage oder den Vorgang abbrechen.|Quellcodeverwaltung VSPackage|Empfohlen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3>|**Projektmappen\-Explorer** und Projekte rufen diese Schnittstelle als Reaktion auf die Aufrufe an, die an die Methoden der Schnittstelle IVstrackProjectDocuments3 gemacht werden.  Die Quellcodeverwaltung VSPackage kann im Batchmodus, synchronisierte Vorgänge mit Lese\-\/Schreibzugriff und Arbeiten mit einer erweiterte `OnQueryAddFiles`\-Methode nachverfolgen.|Quellcodeverwaltung VSPackage|Empfohlen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation>|Diese Schnittstelle stellt Eintragungs verwaltungs Unterstützung für Webprojekte.|Quellcodeverwaltung VSPackage|Empfohlen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip>|Diese Schnittstelle wird verwendet, um QuickInfos für die Quellcodeverwaltung unterliegende Dateien in Projekten zu erhalten.|Quellcodeverwaltung VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl>|Diese Schnittstelle bietet Unterstützung für Namespace.|Quellcodeverwaltung VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution>|VSPackage verwendet diese Schnittstelle, um eine **Neu**\- Namespaceerweiterung in die **Öffnen**, oder **Speichern** Dialogfelder zu integrieren.  Folglich können Projekte zur Quellcodeverwaltung bei der Erstellung automatisch hinzugefügt werden, oder der Quellcodeverwaltung hinzugefügt werden, wenn ein Speichervorgang gültig ist.|Quellcodeverwaltung VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>|VSPackage verwendet diese Schnittstelle, um zusätzliche Symbole als Symbole für Quellcodeverwaltung Knoten in **Projektmappen\-Explorer**zu definieren.|Quellcodeverwaltung VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl>|Das Dialogfeld **Hinzufügen** für Webprojekte verwendet diese Schnittstelle.  Sie stellt Methoden für das Durchsuchen eines Quellcodeverwaltungsspeicherort und zum Öffnen eines Webprojekts bereit, das zuvor im Quellcodeverwaltungsrepository an dieser Stelle hinzugefügt wird.|Quellcodeverwaltung VSPackage|Empfohlen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|Diese Schnittstelle bietet Unterstützung für asynchrones \(Hintergrund\) Laden von Projekten aus der Quellcodeverwaltung aus.|Quellcodeverwaltung VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents>|Diese Schnittstelle ermöglicht Projekte, den Status des asynchronen Ladevorgangs Initiieren von <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>zu überwachen.|Project|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|Diese Schnittstelle kann der IDE, um die aktive Quellcodeverwaltung VSPackage abzufragen.  Die IDE\-Abfragen, die den Wert von Einstellungen für Quellcodeverwaltung die Bedeutung haben, selbst wenn keine aktive Quellcodeverwaltung VSPackage wird registriert wurde.  Diese Schnittstelle wird von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]implementiert und behandelt.|Quellcodeverwaltungs\-Stub|Erforderlich|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>|Diese Schnittstelle wird verwendet, wenn die Quellcodeverwaltung ein VSPackage registriert.|Quellcodeverwaltungs\-Stub|Erforderlich|  
|<xref:EnvDTE.SourceControl>|Diese Schnittstelle ist in der Automatisierung veranschaulicht.  Daher macht sie nur Funktionen, die ausgeführt werden können, ohne eine Benutzeroberfläche anzuzeigen.|Quellcodeverwaltung VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>|Diese Schnittstelle wird verwendet, um die Einstellungen für Quellcodeverwaltung in der Projektmappendatei \(.sln\) zu speichern.  Die Einstellungen zählen die Position der Quellcodeverwaltungs\- Quellcodeverwaltung und den Status des Flags.|Quellcodeverwaltung VSPackage|Empfohlen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>|Diese Schnittstelle wird verwendet, um die Einstellungen für Quellcodeverwaltung die Projektmappen in der Datei zu speichern \(.suo\).  Dies schließt sich benutzerspezifische Einstellungen für Quellcodeverwaltung Eintragungs wie der aktuelle Speicherort des Benutzers ein.|Quellcodeverwaltung VSPackage|Empfohlen|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>|Schließen von Projektmappen oder vor dem Abrufen von neuen Dateien aus der Quellcodeverwaltung diese Schnittstelle wird verwendet, um Ereignisse zu überwachen, um Vorgänge wie Überprüfung in Projektdateien auszuführen, wenn ein Projekt geöffnet wird.|Quellcodeverwaltung VSPackage|Empfohlen|  
  
## Siehe auch  
 [Design\-Elemente](../../extensibility/internals/source-control-vspackage-design-elements.md)