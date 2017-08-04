---
title: "Eigenschaftenseiten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ändern der Eigenschaften von Konfigurationsoptionen"
  - "Eigenschaftenseiten"
  - "Eigenschaftenseiten, Ändern von Konfigurationsoptionen"
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Eigenschaftenseiten
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Benutzer können anzeigen und ändern anlagenabhängige Projekt und unabhängige Eigenschaften die mithilfe der Eigenschaftenseiten.  Eine **Eigenschaftenseiten** Schaltfläche wird im **Eigenschaften** Fenster oder auf der Symbolleiste für Objekte können eine Ansicht die Option Eigenschaftenseiten des ausgewählten Objekts angeben.  Eigenschaftenseiten werden durch die Umgebung erstellt und sind für Projektmappen und Projekte verfügbar.  Sie können jedoch ebenfalls bereitgestellt werden, die für Projektelemente anlagenabhängige Eigenschaften.  Diese Funktion kann verwendet werden, wenn Dateien in einem Projekt unterschiedliche Compilerschalter belegung des schalterfeldes erfordern, ordnungsgemäß zu erstellen.  
  
## Mithilfe der Eigenschaftenseiten  
 Wenn bereits eine Eigenschaftenseite und die Änderungen der Auswahl \(z. B. aus einer Projektmappe ein Projekt für Verbindungen angezeigt wird, ändern sich die Informationen, die in den Seiten angezeigt werden, um die Eigenschaften für die neue Auswahl anzuzeigen.  Wenn keine Eigenschaften für das Objekt vorhanden sind, die Eigenschaftenseiten unterstützen, ist die Eigenschaftenseite leer.  
  
 Wenn mehrere Objekte, die Eigenschaft seitendarstellungen die Schnittmenge von Eigenschaften für alle ausgewählten Elemente ausgewählt.  Wenn das ausgewählte Element nicht anlagenabhängige Eigenschaften enthält und auf die Schaltfläche **Eigenschaftenseiten** auf der Symbolleiste geklickt wird, wird der Fokus auf Eigenschaftenfenster.  Weitere Informationen in Bezug auf das Eigenschaftenfenster und die Auswahl finden Sie unter [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md).  
  
 Wenn Eigenschaften für mehrere Objekte angezeigt werden und Sie einen Wert in einer Eigenschaftenseite ändern, werden alle Werte für die Objekte auf den neuen Wert festgelegt, selbst wenn sie zum ersten Mal unterschiedlich sind, und die Seite leer war, als die Eigenschaften eines einzelnen Objekts angezeigt wurden.  
  
 Es gibt zwei allgemeine Arten von Dialogfeldern **ProjektEigenschaftenseiten** , die in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]verfügbar sind.  Im ersten Beispiel für Visual Basic\-Projekte werden die Eigenschaftenseiten unter Verwendung eines Felds formats, wie im folgenden Bildschirmaufnahme dargestellt angezeigt.  In der zweiten weiter unten in diesem Abschnitt dargestellt, die Eigenschaftenseiten Language Runtime\-Hosts ein Eigenschaftenraster ähnlich dem im Eigenschaftenfenster angezeigt.  
  
 ![Visual Basic&#45;Eigenschaftenseiten](~/extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")  
Dialogfeld Projekt\-Eigenschaftenseiten Format und die Struktur mit Feld  
  
 Die Baumstruktur im Dialogfeld Eigenschaftenseiten wird nicht mit <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>erstellt.  Die Umgebung, in dem die Ebene Namen, der von ihr <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>\-Schnittstellen übergeben wird, erstellt es.  
  
 Es gibt nur zwei Kategorien der obersten Ebene, die auf [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\-Eigenschaftenseiten verfügbar sind:  
  
-   Allgemeine Informationen über konfigurationsunabhängige Eigenschaften, die für das ausgewählte Objekte anzeigt.  Wenn eine der Unterkategorien Allgemeine Eigenschaften ausgewählt ist, sind die Listen Konfiguration und Plattform, Konfigurations\-Manager\-Optionen zum oberen Rand des Dialogfelds nicht verfügbar.  
  
-   Konfigurationseigenschaften, das anlagenabhängige Informationen in Bezug auf Debug\-, Optimierungs\- und Erstellungsparameter für die Projektmappe oder das Projekt enthält.  
  
 Sie können keine weiteren Kategorien erstellen auf der obersten Ebene. Sie können jedoch die Möglichkeit, eine oder das andere in der Implementierung von `IVsPropertyPage`nicht angezeigt.  Wenn Sie z. B. keine CONFIGURATION\-unabhängigen für ein Objekt verfügen, die Eigenschaften anzuzeigen, können Sie festlegen, dass die Kategorie der allgemeinen Eigenschaften nicht angezeigt.  Zeigen Sie allgemeine Eigenschaften angezeigt, wenn `ISpecifyPropertyPages` von dem des Elements und Suchobjekt von Konfigurationseigenschaften implementiert wird, wenn Sie im `ISpecifyPropertyPages` Konfigurationsobjekt \(das Objekt, das `IVsCfg`, `IVsProjectCfg`und verknüpfte Schnittstellen implementiert\).  
  
 Jede Kategorie, die unter der Kategorie der obersten Ebene angezeigt wird, stellt eine separate Seite Eigenschaften dar.  Die Kategorie und Unterkategorie Dateisystemeinträgen, die im Dialogfeld verfügbar sind, werden von der Implementierung von `ISpecifyPropertyPages` und `IVsPropertyPage`bestimmt.  
  
 `IDispatch`\-Objekte für Elemente im Auswahlcontainer, die eine Liste sein, um auf die Eigenschaftenseiten angezeigt werden soll `ISpecifyPropertyPages` implementieren Eigenschaften, die Klassen\-ID aufzulisten.  Der Klassenbezeichner werden als Variablen und übergeben `ISpecifyPropertyPages` werden verwendet, um die Eigenschaftenseiten zu instanziieren.  Die Liste der Klassenbezeichner wird ebenfalls auf `IVsPropertyPage` übergeben, um die hierarchische Struktur auf der linken Seite des Dialogfelds zu erstellen.  Die Eigenschaftenseiten übergeben dann Informationen zurück an den `IDispatch`\-Objekt, das `ISpecifyPropertyPages` implementiert und die Informationen für jede Seite einnimmt.  
  
 Die Eigenschaften des Suchobjekts werden mithilfe `IDispatch` für jedes Objekt im Auswahlcontainer abgerufen.  
  
 Das Implementieren von `Help::DisplayTopicFromF1Keyword` in einem VSPackage stellt die Funktionalität für die Schaltfläche Hilfe verfügbar.  
  
 Weitere Informationen finden Sie unter `IDispatch` und `ISpecifyPropertyPages`in der MSDN Library.  
  
 Der zweite Typ der Eigenschaftenseiten der in den Host. B. ein Formular des Eigenschaftenrasters an, wie im folgenden Bildschirmaufnahme dargestellt.  
  
 ![VC&#45;Eigenschaftenseiten](~/extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")  
Dialogfeld Eigenschaftenseiten mit Eigenschaftenraster  
  
 Die Schnittstellen `IVSMDPropertyBrowser` und `IVSMDPropertyGrid` \(in vsmanaged.h\) deklariert werden verwendet, um das Eigenschaftenraster innerhalb eines Dialogfelds oder eines Fensters zu erstellen und aufzufüllen.  
  
 Die Architektur von Projekten bietet erheblich von den letzten Versionen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]geändert.  Insbesondere aus dem der Begriff Projekts aktiv ist, hat sich geändert.  In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]gibt es kein Konzept eines aktuellen Projekts.  In der vorherigen Entwicklungsumgebung war das aktive Projekt das Projekt, um die Befehle wird standardmäßig unabhängig von dem Kontext erstellen und bereitstellen.  Nun steuert die Projektmappe und übergibt, die Befehle gelten erstellen und bereitstellen, welche Projekte.  
  
 Wie zuvor befand, wird ein aktives Projekt jetzt drei verschiedene Arten aufgezeichnet:  
  
-   Das Startprojekt  
  
     Sie können ein Projekt oder Projekte aus der Eigenschaftenseite der Projektmappe angeben, die gestartet wird, wenn der Benutzer die Taste F5 gedrückt wird oder im Menü Erstellen die Option Ausführen auswählen.  Dies funktioniert auf eine Weise ähnlich dem alten aktiven Projekt im Sinne, dass der Name im Projektmappen\-Explorer angezeigt mit fetter Schriftart ist.  
  
     Sie können das Startprojekt als Eigenschaft im Automatisierungsmodell abrufen, indem Sie `DTE.Solution.SolutionBuild.StartupProjects`aufrufen.  In einem VSPackage rufen Sie das <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> oder die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A>\-Methode auf.  `IVsSolutionBuildManager` ist als Dienst über `QueryService` auf SID\_SVsSolutionBuildManager verfügbar.  Weitere Informationen finden Sie unter [Projekt\-Konfigurationsobjekt](../../extensibility/internals/project-configuration-object.md) und [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md).  
  
-   Buildkonfiguration der aktuellen Projektmappe  
  
     [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verfügt über eine aktive Projektmappenkonfiguration, im Automatisierungsmodell verfügbar ist, indem `DTE.Solution.SolutionBuild.ActiveConfiguration`implementiert.  Eine Projektmappenkonfiguration ist eine Auflistung, die eine Projektkonfiguration für jedes Projekt in der Projektmappe enthält \(jedes Projekt kann mehrere Konfigurationen für mehrere Plattformen mit unähnlichen Namen aufweisen\).  Weitere Informationen in Bezug auf die Eigenschaftenseiten der Projektmappe finden Sie unter [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md).  
  
-   aktuell ausgewählten Projekts  
  
     Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A>\-Methode verwendet, um die Projekthierarchie abzurufen und das Projektelement oder die Elemente, die ausgewählt sind.  Das Design Time Extensibility, DTE würden Sie die `SelectedItems.SelectedItem.Project` und `SelectedItems.SelectedItem.ProjectItem`\-Methoden verwenden.  Es gibt Beispielcode unter diesen Überschriften in den Kern [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Dokumenten.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)   
 [Projekt\-Konfigurationsobjekt](../../extensibility/internals/project-configuration-object.md)   
 [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md)