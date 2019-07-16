---
title: 'Vorgehensweise: Erzwingen von wartbarem Code mit einer Eincheckrichtlinie für die Analyse | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 27593a450f7c2a1b34c1c84bc1d4e7ea5bb5919f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142257"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Vorgehensweise: Erzwingen von verwaltbarem Code mit einer Eincheckrichtlinie für die Codeanalyse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Entwickler können das Codemetrik-Tool verwenden, um die Komplexität und verwaltbarkeit ihres Codes messen, aber sie Codemetrik können nicht als Teil einer Eincheckrichtlinie aufgerufen werden. Allerdings kann ein Team Codeanalyseregeln aktivieren, überprüfen Sie die Kompatibilität ihres Codes mit Codemetrik Standards erzwingen die Regeln durch Check-in-Richtlinien. Weitere Informationen zu codemetriken finden Sie unter den [Codemetrikwerte](../code-quality/code-metrics-values.md).  
  
 Entwickler können die Vererbungstiefe, Klassenkopplung, Wartbarkeitsindex und Komplexitätsregeln zum Erzwingen von wartbarem Code über die Codeanalyse-Eincheckrichtlinien zu ermöglichen. Alle vier dieser Regeln werden in der Codeanalyse Gruppenrichtlinienverwaltungs-Editor unter der Kategorie "Wartbarkeitsregeln" gefunden.  
  
 Kontrolle über die Administratoren der Version für [!INCLUDE[esprfound](../includes/esprfound-md.md)] können die Anforderungen in der Eincheckrichtlinie für die Verwaltbarkeit von Codeanalyseregeln hinzufügen. Diese checken Sie Richtlinien für Entwickler zum Ausführen der Codeanalyse, die auf Grundlage dieser regeländerungen vor dem Initiieren eines benötigen.  
  
### <a name="to-open-the-code-analysis-policy-editor"></a>Der Code Codeanalyserichtlinien-Editor öffnen  
  
1. In **Team Explorer**mit der rechten Maustaste auf das Teamprojekt, klicken Sie auf **Teamprojekteinstellungen**, und klicken Sie dann auf **Quellcodeverwaltung**.  
  
     Die **Quellcodeverwaltung** Dialogfeld wird angezeigt.  
  
2. Auf der **Eincheckrichtlinie** Registerkarte, und klicken Sie auf **hinzufügen**.  
  
     Die **Eincheckrichtlinie hinzufügen** Dialogfeld wird angezeigt.  
  
3. In der **Eincheckrichtlinie** Liste der **Codeanalyse** , und klicken Sie dann auf **OK**.  
  
     Die **Code Codeanalyserichtlinien-Editor** Dialogfeld wird angezeigt.  
  
### <a name="to-enable-code-analysis-maintainability-rules"></a>So aktivieren Sie die Verwaltbarkeit von Codeanalyseregeln  
  
1. In der **Code Codeanalyserichtlinien-Editor** Dialogfeld **Regeleinstellungen**, erweitern Sie die **Wartbarkeitsregeln** Knoten.  
  
2. Wählen Sie die Kontrollkästchen für die folgenden Regeln:  
  
    - Die Tiefe der Vererbung: **CA1501 AvoidExcessiveInheritance** -Schwellenwert: Warnung bei mehr als 5 Ebenen  
  
    - Komplexität: **CA1502 AvoidExcessiveComplexity** -Schwellenwert: Warnung bei mehr als 25  
  
    - Wartbarkeitsindex: **CA1505 AvoidUnmaintainableCode** -Schwellenwert: Warnung bei weniger als 20  
  
    - Klassenkopplung: **CA1506 AvoidExcessiveClassCoupling** -Schwellenwert: Warnung bei mehr als 80 für eine Klasse und mehr als 30 für eine Methode  
  
    - Wählen Sie außerdem, wenn Sie einen Regelverstoß, um einen Build zu verhindern möchten, die **behandeln Warnung als Fehler** Kontrollkästchen neben der Beschreibung der Regel.  
  
3. Klicken Sie auf **OK**. Die neue Richtlinie gilt jetzt Eincheckvorgängen.  
  
## <a name="see-also"></a>Siehe auch  
 [Codemetrikwerte](../code-quality/code-metrics-values.md)   
 [Erstellen und Verwenden von Eincheckrichtlinien für die Codeanalyse](../code-quality/creating-and-using-code-analysis-check-in-policies.md)
