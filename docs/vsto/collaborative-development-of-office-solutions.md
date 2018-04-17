---
title: Gemeinsame Entwicklung von Office-Projektmappen | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], collaborative development
- Office development in Visual Studio, collaboration
- source control [Office development in Visual Studio]
- collaborative development [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 10415a6983c158ae1c117a5b3f9a8b2e1c546a0e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="collaborative-development-of-office-solutions"></a>Gemeinsame Entwicklung von Office-Lösungen
  Mehrere Entwickler können auf einem Office-Projekt auf die gleiche Weise arbeiten, die sie an andere Visual Studio-Projekte zusammenarbeiten. Visual Studio findet die Microsoft Office-Installation auf jedem Computer, selbst wenn Office an verschiedenen Speicherorten installiert ist. Es gibt jedoch einige wichtige Aspekte zu berücksichtigen.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="debug-properties-are-not-shared"></a>Debuggen von Eigenschaften werden nicht freigegeben.  
 In der Quellcodeverwaltung werden Debugeigenschaften nicht für mehrere Benutzer gemeinsam verwendet. Visual Basic- und Visual C#-Projekten speichern die Debugeigenschaften in einer benutzerspezifischen Datei (*Projektname*. vbproj.user oder *Projektname*. csproj.user), und diese Datei wird nicht in der quellcodeverwaltung. Wenn mehrere Personen debuggen, muss jede Person die Debugeigenschaften manuell eingeben.  
  
 Wenn das Projekt auf einer Netzwerkfreigabe statt in der quellcodeverwaltung gespeichert ist, müssen einige zusätzliche Schritte ausgeführt werden, so aktivieren Sie die Entwicklerteams öffnen Sie die Projektmappe, und Testen Sie die Assembly.  
  
## <a name="source-control-requires-checking-out-all-files"></a>Datenquellen-Steuerelements ist erforderlich, alle Dateien auschecken  
 Wenn Sie die quellcodeverwaltung für Ihre Projekte verwenden, sollten Sie sehen Sie sich aller Dateien unter eine Codedatei im **Projektmappen-Explorer** (z. B. die ThisDocument oder ThisWorkbook "ThisAddIn" Code-Dateien) jedes Mal, wenn Sie die Codedatei ändern auch das Dateien, die standardmäßig ausgeblendet sind. Wenn Sie nur die obersten Ebene Codedatei Auschecken, können Ihre Änderungen verloren.  
  
 Nachdem Sie die Änderungen vorgenommen haben, überprüfen Sie, dass alle Dateien in der wieder an. Weitere Informationen zu den ausgeblendeten Codedateien in Projekten, finden Sie unter [Office-Projekte in der Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="security-for-informal-collaboration-on-a-network"></a>Sicherheit für informelle Zusammenarbeit in einem Netzwerk  
 Für alle Projektmappen auf Dokumentebene, die sich in einem Netzwerkverzeichnis befinden (z. B. \\ \\ *Servername*\\*Sharename*), muss der vollqualifizierte Speicherort hinzugefügt werden die Liste vertrauenswürdiger Ordner in der Microsoft Office-Anwendung, mit dem Sie arbeiten. Wählen Sie die Option zum Einschließen der Unterverzeichnisse unter dem Hauptordner oder speziell Debuggen hinzufügen und Erstellen von Ordnern zur Liste vertrauenswürdiger Ordner. Weitere Informationen hierzu finden Sie unter [Gewähren von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md).  
  
 Der temporären Zertifikate, die automatisch, während des Buildvorgangs generiert werden werden Kennwörter nicht gesichert. Die Zertifikate enthalten Benutzernamen des Entwicklers und andere persönliche Informationen. Wenn Sie Anpassungen, die von temporären Zertifikaten signiert werden bereitstellen, möglicherweise andere Benutzer auf diese Informationen zugreifen.  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)   
 [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)   
 [Erstellen von Office-Projektmappen](../vsto/building-office-solutions.md)  
  
  