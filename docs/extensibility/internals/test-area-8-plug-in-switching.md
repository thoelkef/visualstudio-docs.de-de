---
title: Testbereich 8:-Plug-in zu wechseln | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 03e7bd5728320bb2efd0b90728b6c1a16f5997ba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="test-area-8-plug-in-switching"></a>Testbereich 8: Plug-in wechseln
Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE) verfügt über die Benutzeroberfläche (UI) so ändern Sie den Quellcodeverwaltungs-Plug-in. Dieser Testbereich bietet Testfälle für den Prozess der Entnahme das plug-in für die quellcodeverwaltung des Projektmappen verwenden.  
  
## <a name="command-menu-access"></a>Menüzugriff Befehl  
 Die folgenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrated Development-Umgebung im Menüpfade werden in den Testfällen verwendet.  
  
-   Aktuelles Quellcodeverwaltungs-Plug-in: **Tools** -> **Optionen** -> **Quellcodeverwaltung** -> **Plug-in-Auswahl** .  
  
-   Ändern der Quelle Bindung steuern: **Datei** -> **Quellcodeverwaltung** -> **Quellcodeverwaltung ändern**...  
  
## <a name="common-expected-behavior"></a>Allgemeine erwartet  
 Ändern das Quellsteuerelement-Plug-In für eine Projektmappe kann ohne Beenden Sie Visual Studio oder das erneute Laden der Projektmappe zur Verfügung. Darüber hinaus wird der Quellcodeverwaltungs-Plug-in automatisch von einer Lösung verwendet werden, wenn die Projektmappe geladen wird.  
  
## <a name="test-cases"></a>Testfälle  
 Im folgenden finden bestimmte Testfälle für den Plug-in-switching Testbereich.  
  
### <a name="case-8a-automatic-change"></a>Fall 8a: automatisch ändern  
  
#### <a name="expected-behavior"></a>Erwartetes Verhalten  
 Wenn ein Benutzer eine Projektmappe geladen wird, die quellcodeverwaltung unterliegt, die Projektmappe wird automatisch geladen, und der entsprechenden Quelle-Steuerelement-Plug-in als aktuell ausgewählt ist.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Automatische Source Control-Plug-in ändern|1.  Select-Plug-in unter als aktuell testen (**Tools** -> **Optionen** -> **Quellcodeverwaltung** -> **-Plug-in Auswahl**.)<br />2.  Erstellen Sie ein neues Projekt.<br />3.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />4.  Wählen Sie ein anderes plug-in (z. B. [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />5.  Akzeptieren der Aufforderung für entladen Lösung.<br />6.  Öffnen Sie erneut die Projektmappe vom Datenträger.|Lösung wird geöffnet.<br /><br /> -Plug-in unter dem Test wird der Quellcodeverwaltungs-Plug-in.|  
  
### <a name="case-8b-solution-based-change"></a>Case-8 b: Change basierten Lösung  
  
#### <a name="expected-behavior"></a>Erwartetes Verhalten  
 Die Lösung kann seine zugeordneten Datenquellen-Steuerelement-Plug-Ins geändert haben.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Änderung des-Plug-In für eine Projektmappe|1.  Select-Plug-in unter als aktuell testen (**Tools** -> **Optionen** -> **Quellcodeverwaltung** -> **-Plug-in Auswahl**).<br />2.  Erstellen Sie ein neues Projekt und Projektmappe.<br />3.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />4.  Heben Sie die Bindung der Projektmappe aus der quellcodeverwaltung (mithilfe der **Quellcodeverwaltung ändern** Dialogfeld).<br />5.  Wählen Sie ein anderes plug-in (z. B. [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />6.  Laden Sie die Projektmappe vom Datenträger aus, wenn entladen.<br />7.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />8.  Heben Sie die Bindung der Projektmappe aus der quellcodeverwaltung (mit **Quellcodeverwaltung ändern** Dialogfeld).<br />9. Wählen Sie-Plug-in unter dem Test erneut aus.<br />10. Laden Sie Projektmappen vom Datenträger aus, wenn entladen.<br />11. Binden Sie die Projektmappe am ursprünglichen Speicherort (mithilfe der **Quellcodeverwaltung ändern** Dialogfeld).|Lösung wird zur quellcodeverwaltung hinzugefügt, mit dem ausgewählten-Plug-in.|  
  
## <a name="see-also"></a>Siehe auch  
 [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)