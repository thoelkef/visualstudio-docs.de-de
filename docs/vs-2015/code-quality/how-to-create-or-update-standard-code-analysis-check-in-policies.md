---
title: 'Vorgehensweise: Erstellen oder Aktualisieren von Standardeincheckrichtlinien Codeanalyse-Eincheckrichtlinien | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
ms.assetid: 458eb3b8-bb5e-4056-82b7-7079ce9c4089
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6821d218c22f2d83108205d8753fc2d5beac4f28
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939435"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Gewusst wie: Erstellen oder Aktualisieren von Standardeincheckrichtlinien für die Codeanalyse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können anfordern, dass die Codeanalyse auf alle Codeprojekte in einem Teamprojekt mithilfe der Eincheckrichtlinie für die Analyse ausgeführt werden. Codeanalyse erfordert, kann die Qualität des Codes verbessern, die in die CodeBase überprüft wird.  
  
> [!NOTE]
>  Dieses Feature ist nur verfügbar, wenn Sie Team Foundation Server verwenden.  
  
 Eincheckrichtlinien für die Analyse in den teamprojekteinstellungen festgelegt werden und gelten für jedes Codeprojekt im Teamprojekt. Codeanalysen werden bei Projekten mit Code in der Projektdatei (XXPROJ) für das Codeprojekt konfiguriert. Codeanalysen werden auf dem lokalen Computer ausgeführt. Wenn Sie eine Eincheckrichtlinie für die Analyse ermöglichen, Dateien in einem Codeprojekt, die eingecheckt werden, nach ihrer letzten Bearbeitung kompiliert werden müssen und eine Codeanalyse ausgeführt werden, mindestens enthält müssen die Regeln in den teamprojekteinstellungen auf dem Computer ausgeführt werden, in c Änderungen es wurden vorgenommen.  
  
- Für verwalteten Code, Festlegen der Check-in-Richtlinie durch Angabe einer *Regelsatz* , enthält eine Teilmenge der Regeln für die Codeanalyse.  
  
- Für C/C++-Code erfordert die Check-in-Richtlinie an, dass alle Regeln für die Codeanalyse ausgeführt werden. Sie können die präprozessoranweisungen deaktivieren bestimmte Regeln für die einzelne Codeprojekte in Ihrem Teamprojekt hinzufügen.  
  
  Nachdem Sie eine Eincheckrichtlinie für verwalteten Code angegeben haben, können Teammitglieder ihre codeanalyseeinstellungen für Codeprojekte an den Richtlinieneinstellungen für Team-Projekt synchronisieren.  
  
### <a name="to-open-the-check-in-policy-editor"></a>Die Check-in Gruppenrichtlinienverwaltungs-Editor öffnen  
  
1.  In Team Explorer mit der Maustaste den Namen des Teamprojekts, zeigen Sie auf **Teamprojekteinstellungen**, und klicken Sie dann auf **Quellcodeverwaltung**.  
  
2.  In der **Quellcodeverwaltung** wählen Sie im Dialogfeld die **Eincheckrichtlinie** Registerkarte.  
  
3.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Klicken Sie auf **hinzufügen** zum Erstellen einer neuen Check-in-Richtlinie.  
  
    -   Doppelklicken Sie auf die vorhandene **Codeanalyse** Element in der **Richtlinientyp** Liste, um die Richtlinie zu ändern.  
  
### <a name="to-set-policy-options"></a>Festlegen von Optionen  
  
-   Aktivieren Sie oder deaktivieren Sie die folgenden Optionen:  
  
    |Option|Beschreibung|  
    |------------|-----------------|  
    |**Erzwingen Sie, um nur die Dateien enthalten, die Teil der aktuellen Projektmappe eingecheckt.**|Codeanalyse kann nur auf Dateien in Projektmappen und Projektdateien Konfigurationsdateien angegeben ausgeführt. Diese Richtlinie wird sichergestellt, dass sämtlicher Code, der Teil einer Projektmappe wird analysiert wird.|  
    |**C/C++-Codeanalyse erzwingen (/ analyze)**|Erfordert, dass alle C- oder C++-Projekte erstellt werden, mit dem / analyze-Compileroption, um die Codeanalyse ausgeführt wird, bevor sie eingecheckt werden können.|  
    |**Codeanalyse für verwalteten Code erzwingen**|Erfordert, dass alle verwalteten Projekte odeanalyse ausführen und zu erstellen, bevor sie eingecheckt werden können.|  
  
-  
  
### <a name="to-specify-a-managed-rule-set"></a>Um einen verwalteten Regelsatz anzugeben.  
  
-   Von der **diesen Regelsatz ausführen** aufzulisten, verwenden Sie eine der folgenden Methoden:  
  
    -   Wählen Sie einen Microsoft-standard-Regelsatz.  
  
    -   Klicken Sie zum Auswählen eines benutzerdefinierten Regelsatzes auf  **\<Regelsatz auswählen aus der Quellcodeverwaltung... >**, und geben Sie dann auf den Versionskontrollpfad des Regelsatzes in der Quelle-Browser-Steuerelement. Die Syntax der einen Pfad für die Versionskontrolle ist:  
  
    -   **$/** `TeamProjectName` **/** `VersionControlPath`  
  
    -   Weitere Informationen zum Erstellen und Implementieren einer benutzerdefinierte Eincheckrichtlinie Regel festlegen, finden Sie unter [Implementieren von benutzerdefinierten Eincheckrichtlinien für verwalteten Code](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Verwenden von Eincheckrichtlinien für die Codeanalyse](../code-quality/creating-and-using-code-analysis-check-in-policies.md)



