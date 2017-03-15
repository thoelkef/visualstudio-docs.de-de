---
title: "Auswahl und W&#228;hrung, in der IDE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Währung, Visual Studio-IDE"
  - "Auswahl-IDE"
  - "Auswahl, Visual Studio-IDE"
  - "Currency-IDE"
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Auswahl und W&#228;hrung, in der IDE
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung \(IDE\) verwaltet Informationen über Benutzer aktuell ausgewählten Objekten mit *Kontext*. Mit Auswahlkontext können VSPackages Währung auf zweierlei Weise nachverfolgen teilnehmen:  
  
-   Durch die Weitergabe von Währungsinformationen über die VSPackages der IDE.  
  
-   Durch die Überwachung der Benutzer derzeit aktiven Auswahl in der IDE.  
  
## Auswahlkontext  
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE Global verfolgt des IDE\-Währung in eigene globale Auswahl Context\-Objekt. Die folgende Tabelle zeigt die Elemente, die den Auswahlkontext bilden.  
  
|Element|Beschreibung|  
|-------------|------------------|  
|Aktuelle Hierarchie|In der Regel das aktuelle Projekt. eine aktuelle NULL\-Hierarchie gibt an, dass die Projektmappe als Ganzes aktuell ist.|  
|Aktuelle ' ItemId '|Das ausgewählte Element in der aktuellen Hierarchie; Wenn mehrere Auswahl klicken Sie im Fenster Projekt vorhanden sind, können mehrere aktuelle Elemente vorhanden sein.|  
|Aktuelle `SelectionContainer`|Enthält ein oder mehrere Objekte, die für die Eigenschaften im Eigenschaftenfenster angezeigt werden soll.|  
  
 Darüber hinaus verwaltet die Umgebung zwei globale Listen:  
  
-   Eine Liste der aktiven UI\-Befehls\-IDs  
  
-   Eine Liste der derzeit aktiven Elementtypen.  
  
### Fenstertypen und Auswahl  
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE Windows in zwei allgemeine Arten organisiert:  
  
-   Windows Hierarchy\-Datentyp  
  
-   Rahmenfenster, wie Tool\-und Dokumentfenster  
  
 Die IDE verfolgt Währung unterschiedlich für jedes dieser Fenster Typen.  
  
 Die am häufigsten verwendete Projekttyp\-Fenster wird im Projektmappen\-Explorer die IDE steuert. Ein Projekttyp\-Fenster verfolgt die globalen Hierarchie und Element\-ID des Kontexts globale Auswahl und das Fenster abhängig von der Auswahl des Benutzers die aktuelle Hierarchie bestimmt. Für Windows Projekttyp, die Umgebung global Service bietet <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>, über welche VSPackages können die aktuellen Werte für geöffneten Elemente überwachen. Eigenschaft, die in der Umgebung durchsuchen wird von diesem globalen Dienst gesteuert.  
  
 Rahmenfenster verwenden auf der anderen Seite DocObject innerhalb des Rahmenfensters SelectionContext\-Wert \(der Hierarchie\/ItemID\/SelectionContainer durchdachter\) übertragen. . Rahmenfenster verwenden Sie den Dienst <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> für diesen Zweck. Die DocObject kann nur Werte für den Auswahlcontainer übertragen und die lokalen Werte für die Hierarchie und Element\-ID unverändert, typisch für MDI\-untergeordneten Dokumente.  
  
### Ereignisse und Währung  
 Zwei Arten von Ereignissen auftreten, die die Umgebung Konzept der Währung beeinflussen:  
  
-   Ereignisse, die auf globaler Ebene weitergegeben werden und Fensterkontext Frame Auswahl zu ändern. Beispiele für diese Art von Ereignis sind ein untergeordnetes MDI\-Fenster geöffnet wird, eine globale Toolfenster geöffnet wird, oder ein Projekttyp\-Fenster geöffnet wird.  
  
-   Ereignisse, die die Elemente im Fenster Frame Auswahlkontext verfolgt ändern. Beispiele: Ändern der Auswahl in einem DocObject oder Ändern der Auswahl in einem Projekttyp\-Fenster.  
  
## Siehe auch  
 [Auswahl Kontextobjekte](../../extensibility/internals/selection-context-objects.md)   
 [Feedback an den Benutzer](../../extensibility/internals/feedback-to-the-user.md)