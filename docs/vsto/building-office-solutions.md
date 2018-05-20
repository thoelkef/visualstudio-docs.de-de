---
title: Erstellen von Office-Projektmappen
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- debugging [Office development in Visual Studio]
- debugging Office applications in Visual Studio
- solutions [Office development in Visual Studio], debugging
- Office applications [Office development in Visual Studio], debugging
- application development [Office development in Visual Studio], building
- Office applications [Office development in Visual Studio], building
- projects [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], building
- solutions [Office development in Visual Studio], building
- Office projects [Office development in Visual Studio], debugging
- projects [Office development in Visual Studio], building
- builds [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], building
- application development [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], debugging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c4adafc1acfda949a16a3daa3db8da2e96eba2d0
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="build-office-solutions"></a>Erstellen von Office-Projektmappen
  Im Allgemeinen ist das Erstellen und Debuggen von Office-Projekten mit dem Erstellen und Debuggen von anderen Projekttypen in Visual Studio identisch, z. B. von Windows Forms. Die vorhandenen Unterschiede werden in diesen Themen des Abschnitts erläutert. Allgemeine Informationen zum Erstellen von Anwendungen finden Sie unter [kompilieren und erstellen Sie in Visual Studio](/visualstudio/ide/compiling-and-building-in-visual-studio).  
  
> [!NOTE]  
>  Bei der Entwicklung von Lösungen, die über die Office-Erfahrungen erweitern "interested" [mehrere Plattformen](https://dev.office.com/add-in-availability)? Sehen Sie sich die neue [Office-Add-ins Modell](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office-Add-ins haben einen geringen Ressourcenbedarf im Vergleich zu VSTO-add-ins und Lösungen, und Sie können sie mithilfe von fast allen Web-Technologien, wie HTML5, JavaScript, CSS3 und XML-Programmierung erstellen.  
  
## <a name="project-output-for-office-projects"></a>Projektausgabe für Office-Projekten  
 Der Ausgabeort für Office-Projekte ist „ *Projektname*\bin\release“ oder „ *Projektname*\bin\debug“. Sie können die Erstellung nicht in einem Bereitstellungsverzeichnis vornehmen.  
  
### <a name="document-level-projects"></a>Projekte auf Dokumentebene  
 Wenn Sie ein Projekt auf Dokumentebene erstellen, sind die folgenden Elemente in der Projektausgabe enthalten:  
  
-   Eine Kopie des Projektdokuments.  
  
-   Die Projektassembly und alle referenzierten Assemblys, deren **Lokale Kopie** -Eigenschaft auf **true**festgelegt ist.  
  
-   Das Anwendungsmanifest, besitzt die Dateierweiterung *.manifest*. Weitere Informationen finden Sie unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
-   Das Bereitstellungsmanifest, das die Dateinamenerweiterung *".VSTO"*. Weitere Informationen finden Sie unter [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md).  
  
-   Eine Programmdatenbank (*PDB*) Datei.  
  
> [!NOTE]  
>  Wenn Sie eine Projektmappe auf Dokumentebene an einem Remotespeicherort anstatt auf dem lokalen Computer erstellen, fügen Sie den vollqualifizierten Pfad zur Liste vertrauenswürdiger Speicherorte im Vertrauensstellungscenter der Anwendung hinzu. Weitere Informationen finden Sie im Abschnitt Gewähren von Vertrauenswürdigkeit für Dokumente in [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md).  
  
### <a name="application-level-projects"></a>Projekte auf Anwendungsebene  
 Wenn Sie ein VSTO Add-In-Projekt erstellen, sind die folgenden Elemente in der Projektausgabe enthalten:  
  
-   Die Projektassembly und alle referenzierten Assemblys, deren **Lokale Kopie** -Eigenschaft auf **true**festgelegt ist.  
  
-   Das Anwendungsmanifest, besitzt die Dateierweiterung *.manifest*. Weitere Informationen finden Sie unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
-   Das Bereitstellungsmanifest, das die Dateinamenerweiterung *".VSTO"*. Weitere Informationen finden Sie unter [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md).  
  
-   Eine Programmdatenbank (*PDB*)-Datei für die Projektassembly.  
  
 Der Buildprozess für VSTO-Add-In-Projekte erstellt auch einen Satz von Registrierungseinträgen auf dem Entwicklungscomputer, die zum Laden des VSTO-Add-Ins erforderlich sind. Weitere Informationen finden Sie unter [Registrierungseinträge für VSTO-Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).  
  
 Wenn Sie ein VSTO-Add-In-Projekt für Outlook erstellen, das Formularbereiche enthält, werden die folgenden Informationen vom Buildprozess zur Registrierung hinzugefügt:  
  
-   Einen Schlüssel für jede Nachrichtenklasse, die mindestens einem Formularbereich zugeordnet ist.  
  
-   Einen Eintrag für jeden Formularbereich und einen zugeordneten Wert, der den Namen des Outlook VSTO-Add-Ins darstellt.  
  
 Outlook benötigt diese Informationen zum Laden der Formularbereiche.  
  
## <a name="referenced-assemblies"></a>Assemblys, auf die verwiesen wird  
 Sie können aus Ihrem Projekt „Erstellen von Office-Projektmappen“ auf Assemblys verweisen (einschließlich Klassenbibliotheksprojekte). Jede referenzierte Assembly enthält eine Eigenschaft namens **Lokale Kopie**. **Lokale Kopie** gibt an, ob die Assembly in das Ausgabeverzeichnis kopiert wird. In der Standardeinstellung ist die Eigenschaft auf **true**festgelegt. Jede referenzierte Assembly, bei der **Lokale Kopie** auf **true** festgelegt ist, wird in das Ausgabeverzeichnis kopiert.  
  
## <a name="security-during-the-build-process"></a>Sicherheit während des Buildprozesses  
 Visual Studio konfiguriert automatisch die Sicherheitseinstellungen auf dem Entwicklungscomputer, um während des Buildprozesses der Projektmappe Vertrauenswürdigkeit zu gewähren. Dadurch kann die Projektmappe beim Debuggen ausgeführt werden.  
  
 Office-Projekte verwenden Zertifikate, um den Herausgeber zu überprüfen. Visual Studio erstellt automatisch ein temporäres Zertifikat zur Identifizierung von Office-Projektmappen und konfiguriert den Entwicklungscomputer, damit dem temporären Zertifikat vertraut wird.  
  
 Weitere Informationen finden Sie unter [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md).  
  
### <a name="network-projects"></a>Netzwerkprojekte  
 Wenn sich der Speicherort der Assembly oder des Dokuments auf einer Netzwerkfreigabe befindet, ist die Aktualisierung der lokalen Sicherheitsrichtlinie (auf Benutzerebene) nicht ausreichend, um die Ausführung der Projektmappe zu gestatten. Ein Administrator muss Assemblys und Dokumenten, die sich auf einer Netzwerkfreigabe befinden, volle Vertrauenswürdigkeit auf Computerebene gewähren, bevor die Projektmappe ausgeführt werden kann. Weitere Informationen zum Festlegen der Sicherheitsrichtlinie finden Sie unter [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md).  
  
 Für Projekte auf Dokumentebene müssen Sie außerdem den vollqualifizierten Speicherort des Dokuments zur Office-Liste vertrauenswürdiger Ordner hinzufügen. Weitere Informationen finden Sie unter [Gewähren von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md).  
  
## <a name="change-the-platform-target"></a>Ändern der Zielplattform  
 Standardmäßig ist die Zielplattform für Office-Projekte **Beliebige CPU**. In der Regel sollten Sie diese Einstellung nicht ändern. Office-Projektmappen, die mit der Zielplattformeinstellung **Beliebige CPU** erstellt werden, werden in 32-Bit- und 64-Bit-Versionen von Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] oder [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]ausgeführt.  
  
 Sie sollten die Zielplattform nur auf x64 festlegen, wenn Sie eine Projektmappe erstellen, die nur in 64-Bit-Versionen von Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] oder [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]ausgeführt wird, und die Projektmappe systemeigene 64-Bit-APIs aufruft. Weitere Informationen zum Ändern der zielplattformeinstellung finden Sie unter [Vorgehensweise: Konfigurieren von Projekten für Zielplattformen](../ide/how-to-configure-projects-to-target-platforms.md).  
  
 Wenn Sie für die Zielplattform x64 festlegen, kann die Projektmappe nicht in 32-Bit-Versionen von Windows oder Office ausgeführt werden. Die x64-Zielplattform erfordert, dass die Projektmappe in einem 64-Bit-Prozess ausgeführt wird.  
  
## <a name="use-the-clean-command"></a>Verwenden Sie den Befehls "bereinigen"  
 Um die erstellten Projektdateien vom Entwicklungscomputer zu entfernen, können Sie den Befehl **Bereinigen** aus dem Menü **Erstellen** in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]verwenden. Der Befehl **Bereinigen** löscht alle Dateien im Ausgabespeicherort des Builds. Für Projekte auf Anwendungsebene entfernt der Befehl **Bereinigen** auch die vom Buildprozess erstellten Registrierungseinträge.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Debuggen von Office-Projekten](../vsto/debugging-office-projects.md)|Beschreibt Probleme beim Debuggen von Office-Projekten.|  
|[Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokumentebene für Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Veranschaulicht, wie Sie eine Standardanpassung auf Dokumentebene für Excel erstellen.|  
|[Vorgehensweise: Reaktivieren eines VSTO-Add-Ins, das deaktiviert wurde](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|Beschreibt der erneute Aktivieren eines zuvor hart oder weich deaktivierten VSTO-Add-Ins.|  
|[Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)|Enthält Links zu Informationen über das Erstellen von Office-Projektmappen und über die Aufgabe, die Assemblys dabei zukommt.|  
  
  