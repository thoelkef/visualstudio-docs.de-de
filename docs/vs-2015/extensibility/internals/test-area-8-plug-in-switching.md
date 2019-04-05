---
title: 'Testbereich 8: Plug-in-Wechsel | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8064ffec4b98c1a05d8236b11bec226a08f20321
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58956180"
---
# <a name="test-area-8-plug-in-switching"></a>Testbereich 8: Plug-In-Wechsel
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrierte Entwicklungsumgebung (IDE) verfügt über die Benutzeroberfläche (UI) so ändern Sie das aktuelle Quellcodeverwaltungs-Plug-in. Dieser Testbereich bietet Testfälle für den Prozess auswählen, die für die Verwendung für die quellcodeverwaltung des Projektmappen-Plug-in.  
  
## <a name="command-menu-access"></a>Menüzugriff Befehl  
 Die folgenden [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrierte Development-Umgebung im Menüpfade werden verwendet, in den Testfällen.  
  
-   Quellcodeverwaltungs-Plug-in: **Tools** -> **Optionen** -> **Quellcodeverwaltung** -> **Plug-in-Auswahl**.  
  
-   Quelle ändern Bindung steuern: **Datei** -> **Quellcodeverwaltung** -> **ändern, Datenquellen-Steuerelement**...  
  
## <a name="common-expected-behavior"></a>Allgemeine erwartet  
 Ändern das Quellcodeverwaltungs-Plug-In für eine Lösung ist möglich, ohne Visual Studio beenden oder das erneute Laden der Projektmappe. Darüber hinaus wird das aktuelle Quellcodeverwaltungs-Plug-in automatisch von einer Lösung verwendet werden, wenn diese Projektmappe geladen ist.  
  
## <a name="test-cases"></a>Testfälle  
 Im folgenden finden bestimmte Testfälle für den-Plug-in durch den Wechsel des Testbereich.  
  
### <a name="case-8a-automatic-change"></a>Groß-/Kleinschreibung 8a: Automatische Änderung  
  
#### <a name="expected-behavior"></a>Es wird erwartet  
 Wenn ein Benutzer eine Projektmappe geladen wird, die unter quellcodeverwaltung befindet, die Projektmappe wird automatisch geladen, und das entsprechende Quellcodeverwaltungs-Plug-in als aktuell ausgewählt ist.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Automatische Source Control-Plug-in ändern|1.  Select-Plug-in als aktuell testen (**Tools** -> **Optionen** -> **Quellcodeverwaltung** -> **-Plug-in Auswahl**.)<br />2.  Erstellen Sie ein neues Projekt.<br />3.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />4.  Wählen Sie eine andere-Plug-in (z. B. [!INCLUDE[vsvss](../../includes/vsvss-md.md)]).<br />5.  Akzeptieren Sie entladen Lösung-Eingabeaufforderung.<br />6.  Öffnen Sie die Projektmappe vom Datenträger aus.|Projektmappe wird geöffnet.<br /><br /> -Plug-in im Test wird das aktuelle Quellcodeverwaltungs-Plug-in.|  
  
### <a name="case-8b-solution-based-change"></a>Groß-/Kleinschreibung 8 b: Informationsreiche lösungsbasierte ändern  
  
#### <a name="expected-behavior"></a>Es wird erwartet  
 Die Lösung kann die zugehörige Quellcodeverwaltungs-Plug-in geändert haben.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Änderung des-Plug-In für eine Projektmappe|1.  Select-Plug-in als aktuell testen (**Tools** -> **Optionen** -> **Quellcodeverwaltung** -> **-Plug-in Auswahl**).<br />2.  Erstellen Sie ein neues Projekt und Projektmappe.<br />3.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />4.  Aufheben der Bindung der Projektmappe aus der quellcodeverwaltung (mithilfe der **Quellcodeverwaltung ändern** (Dialogfeld)).<br />5.  Wählen Sie eine andere-Plug-in (z. B. [!INCLUDE[vsvss](../../includes/vsvss-md.md)]).<br />6.  Laden Sie die Projektmappe vom Datenträger aus, wenn entladen.<br />7.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />8.  Aufheben der Bindung der Projektmappe aus der quellcodeverwaltung (mit **Quellcodeverwaltung ändern** (Dialogfeld)).<br />9. Wählen Sie-Plug-in im Test erneut aus.<br />10. Laden Sie die Projektmappe vom Datenträger erneut, wenn entladen.<br />11. Binden Sie die Lösung am ursprünglichen Speicherort (mithilfe der **Quellcodeverwaltung ändern** (Dialogfeld)).|Projektmappe wird zur quellcodeverwaltung hinzugefügt, mit dem ausgewählten-Plug-in.|  
  
## <a name="see-also"></a>Siehe auch  
 [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
