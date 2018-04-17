---
title: Auswahl und Währung, in der IDE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bf8c58cb08f82b10970424600843b0fedcf477fc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="selection-and-currency-in-the-ide"></a>Auswahl und Währung, in der IDE
Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE) verwaltet Informationen zu Benutzer ausgewählte Objekte derzeit mit der Auswahl *Kontext*. Bei Auswahlkontext können VSPackages Teil in Währung nachverfolgen auf zwei Arten verwendet werden:  
  
-   Durch Weitergabe Währungsinformationen zu den VSPackages der IDE an.  
  
-   Durch Überwachen der Benutzer derzeit aktiven Auswahlen in der IDE.  
  
## <a name="selection-context"></a>Auswahlkontext  
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE Global der nachverfolgt IDE Währung in einem eigenen globalen Auswahl Context-Objekt. Die folgende Tabelle zeigt die Elemente, aus denen die Auswahlkontext besteht.  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Aktuelle Hierarchie|In der Regel auf das aktuelle Projekt; eine aktuelle Hierarchie von NULL gibt an, dass die Projektmappe als Ganzes aktuell sind.|  
|Aktuelle ItemID|Das ausgewählte Element in der aktuellen Hierarchie; Wenn mehrere Optionen auswählen, geben Sie im Projekt sind, können mehrere aktuelle Elemente vorhanden sein.|  
|Aktuelle `SelectionContainer`|Enthält eine oder mehrere Objekte, die für die Eigenschaften im Eigenschaftenfenster angezeigt werden soll.|  
  
 Darüber hinaus behält die Umgebung zwei globale Listen:  
  
-   Eine Liste der aktiven UI-Befehls-IDs  
  
-   Eine Liste der derzeit aktiven Elementtypen.  
  
### <a name="window-types-and-selection"></a>Fenstertypen und Auswahl  
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE Windows in zwei allgemeine Arten organisiert:  
  
-   Hierarchy-Datentyp windows  
  
-   Z. B. Tool-und Dokumentfenster Rahmenfenstern  
  
 Die IDE verfolgt Währung anders für jedes dieser Fenster Typen.  
  
 Die am häufigsten verwendete Projekttyp Fenster wird im Projektmappen-Explorer, die steuert, die IDE. Ein Projekttyp Fenster nachverfolgt, die globalen Hierarchie und Element-ID des Kontexts globalen Auswahl, und das Fenster benötigt die Auswahl des Benutzers zum Bestimmen der aktuellen Hierarchie. Für Windows Projekttyp, stellt die Umgebung global Service <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>, bis die VSPackages können die aktuellen Werte für geöffneten Elemente überwachen. Eigenschaft, die in der Umgebung durchsuchen wird von diesem globalen Dienst gesteuert.  
  
 Rahmenfenster, verwenden die DocObject andererseits, innerhalb des Rahmenfensters SelectionContext-Wert (der Hierarchie/ItemID/SelectionContainer Trio) mithilfe von Push übertragen. sein. Rahmenfenster Nutzung des Diensts <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> für diesen Zweck. DocObject kann nur die Werte für den Auswahlcontainer push verlassen die lokalen Werte für die Hierarchie und Element-ID unverändert, wenn für MDI-untergeordneten Dokumente typisch ist.  
  
### <a name="events-and-currency"></a>Ereignisse und Währung  
 Zwei Typen von Ereignissen auftreten, die die Umgebung Konzept Währung beeinflussen:  
  
-   Ereignisse, die auf globaler Ebene weitergegeben werden, und ändern die Fenster Frame Auswahlkontext. Beispiele für diese Art von Ereignis sind ein untergeordnetes MDI-Fenster geöffnet, eine globale Toolfenster geöffnet wird, oder einem Projekttyp Toolfenster geöffnet wird.  
  
-   Ereignisse, die die Elemente im Fenster Frame Auswahlkontext verfolgt ändern. Beispiele: Ändern der Auswahl in einem DocObject oder Ändern der Auswahl in einem Projekttyp Fenster.  
  
## <a name="see-also"></a>Siehe auch  
 [Auswahl Kontextobjekte](../../extensibility/internals/selection-context-objects.md)   
 [Feedback an den Benutzer](../../extensibility/internals/feedback-to-the-user.md)