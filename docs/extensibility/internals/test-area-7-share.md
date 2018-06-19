---
title: 'Testbereich 7: Freigeben | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa74d6ff2291288a1ca0e7f17a2edb1e126f222b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142467"
---
# <a name="test-area-7-share"></a>Testbereich 7: Freigabe
Dieser Testbereich behandelt Freigeben von Elementen zwischen den Standorten über die **Freigabe** Befehl.  
  
 Ein Hhare-Vorgang wird die offensichtlichen Duplizierung von Dateien und Ordnerelemente zwischen zwei oder mehr Standorten innerhalb einer Quellhierarchie für die-Steuerelement. Duplizierung erfolgt nicht tatsächlich auf dem Server, jedoch sieht der Benutzer dieselbe Datei in zwei oder mehr angegebenen Speicherorten. Wenn keines der freigegebene Elemente geändert werden, werden diese Änderungen an allen anderen freigegebenen Speicherorten angezeigt.  
  
 Freigeben von Ordnern funktioniert, wenn Sie einen Ordner mit mindestens einer Datei unter quellcodeverwaltung darin auswählen. Share-Befehl ist deaktiviert, in den folgenden Situationen:  
  
-   Wenn der ausgewählte Ordner einem leeren Ordner ist.  
  
-   Wenn ein echter Ordner vorhanden ist, aber es keine Quelldateien für das Steuerelement enthält.  
  
-   Wenn ein virtueller Ordner vorhanden ist, ob quellcodeverwalteten Dateien darin oder nicht.  
  
-   Ist ein Webprojekt für Remote-Website.  
  
## <a name="command-menu-access"></a>Menüzugriff Befehl  
 Die folgenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrated Development-Umgebung im Menüpfade werden in den Testfällen verwendet.  
  
 Freigabe: **Datei**->**Quellcodeverwaltung**->**Freigabe**.  
  
## <a name="expected-behavior"></a>Erwartetes Verhalten  
  
-   Freigegebene Datei, die in freigegebenen Speicherort wird angezeigt.  
  
-   Anzeigen der Quelle-Steuerelement Version Store Verlauf zeigt an, dass Dateien gesichert freigegeben werden.  
  
-   Bearbeiten einer freigegebenen Datei bearbeitet beide Speicherorte der Datei.  
  
## <a name="test-cases"></a>Testfälle  
 Im folgenden finden bestimmte Testfälle zum Bereich "Freigabe Test".  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Teilen Sie eine Datei aus einem geladenes Projekt unter quellcodeverwaltung zu einem anderen geladenen Projekt|1.  Erstellen Sie ein neues Projekt.<br />2.  Fügen Sie der Projektmappe ein zweites Projekt hinzu.<br />3.  Erstellen Sie eine Datei in das zweite Projekt mit einem Namen, der nicht im ersten Projekt vorhanden ist.<br />4.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />5.  Wählen Sie das erste Projekt.<br />6.  Open **Freigabe** (Dialogfeld) (**Datei** -> **Quellcodeverwaltung** -> **Freigabe**).<br />7.  Die Datei aus dem zweiten Projekt auf das erste Projekt frei.<br />8.  Akzeptieren Sie **Auschecken** Wenn Sie aufgefordert werden.|Allgemeine erwartet.|  
|Eine Datei aus einem Projekt auf einen anderen Teilen|1.  Erstellen Sie ein neues Projekt.<br />2.  Zur quellcodeverwaltung hinzufügen.<br />3.  Schließen Sie die Projektmappe.<br />4.  Erstellen Sie ein zweites Projekt (neue Lösung).<br />5.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />6.  Wählen Sie das Projekt.<br />7.  Öffnen der **Freigabe** (Dialogfeld) (**Datei** -> **Quellcodeverwaltung** -> **Freigabe**).<br />8.  Teilen Sie eine Datei aus dem zuvor hinzugefügten Projekt dem geöffneten Projekt.<br />9. Akzeptieren Sie **Auschecken** Wenn Sie aufgefordert werden.|Allgemeine erwartet.|  
|Teilen Sie eine Datei nicht Teil eines Projekts aus der quellcodeverwaltung in die aktuell geladenes Projekt|1.  Erstellen Sie ein neues Projekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Fügen Sie eine Datei zur quellcodeverwaltung, die nicht Teil des Projekts oder der Projektmappe ist.<br />4.  Wählen Sie das Projekt, und öffnen Sie die **Freigabe** (Dialogfeld) (**Datei** -> **Quellcodeverwaltung** -> **Freigabe**).<br />5.  Wählen Sie eine Datei innerhalb der **freigeben** (Dialogfeld), die nicht in das aktuelle Projekt oder die Projektmappe vorhanden sein, und teilen Sie diese.<br />6.  Akzeptieren Sie **Auschecken** Wenn Sie aufgefordert werden.|Speicher der quellcodeverwaltung hat einen GET-Befehl ausgeführt werden, damit die Datei jetzt am lokalen Speicherort des Projekts befindet.|  
|Freigeben von Dateien im selben Projekt in einen anderen Ordner|1.  Wählen Sie **automatisch Auschecken** in **Tools** -> **Optionen** -> **Quellcodeverwaltung**.<br />2.  Erstellen eines neuen Projekts, und es zur quellcodeverwaltung hinzufügen.<br />3.  Fügen Sie dem Projekt einen Ordner hinzu.<br />4.  Fügen Sie eine Datei in den Ordner, und überprüfen Sie im Ordner "".<br />5.  Wählen Sie den Ordner an.<br />6.  Open **Freigabe** (Dialogfeld) (**Datei** -> **Quellcodeverwaltung** -> **Freigabe**).<br />7.  Datei in den ausgewählten Ordner frei.|Allgemeine erwartet.<br /><br /> Ordner muss sich eine Datei mit überprüft werden, bevor er für die Freigabe verwendet werden kann.|  
|Freigeben eines Ordners in das geladene Projekt – rekursive|1.  Erstellen Sie ein neues Projekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Wählen Sie das Projekt.<br />4.  Öffnen der **Freigabe** (Dialogfeld) (**Datei** -> **Quellcodeverwaltung** -> **Freigabe**).<br />5.  Wählen Sie einen Ordner.<br />6.  Teilen Sie die Ordner rekursiv in das Projekt ein.|Allgemeine erwartet.|  
|Mehrere Dateien von einem Projekt in eine andere freigeben|1.  Erstellen Sie ein neues Projekt mit mehreren Dateien.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Schließen Sie die Projektmappe.<br />4.  Erstellen Sie ein neues Projekt in einer neuen Projektmappe ein.<br />5.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />6.  Wählen Sie das Projekt.<br />7.  Öffnen der **Freigabe** (Dialogfeld) (**Datei** -> **Quellcodeverwaltung** -> **Freigabe**).<br />8.  Freigeben Sie mehrere Dateien aus dem zuvor erstellten Projekt dem aktuell geöffneten Projekt.|Allgemeine erwartet.|  
  
## <a name="see-also"></a>Siehe auch  
 [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)