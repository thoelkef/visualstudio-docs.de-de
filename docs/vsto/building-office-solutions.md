---
title: "Aktualisieren von Office-Projektmappen"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Debuggen [Office-Entwicklung in Visual Studio]"
  - "Debuggen von Office-Anwendungen in Visual Studio"
  - "Projektmappen [Office-Entwicklung in Visual Studio], Debuggen"
  - "Office-Anwendungen [Office-Entwicklung in Visual Studio], Debuggen"
  - "Anwendungsentwicklung [Office-Entwicklung in Visual Studio], Erstellen"
  - "Office-Anwendungen [Office-Entwicklung in Visual Studio], Erstellen"
  - "Projekte [Office-Entwicklung in Visual Studio], Debuggen"
  - "Office-Projektmappen [Office-Entwicklung in Visual Studio], Erstellen"
  - "Projektmappen [Office-Entwicklung in Visual Studio], Erstellen"
  - "Office-Projekte [Office-Entwicklung in Visual Studio], Debuggen"
  - "Projekte [Office-Entwicklung in Visual Studio], Erstellen"
  - "Builds [Office-Entwicklung in Visual Studio]"
  - "Office-Projekte [Office-Entwicklung in Visual Studio], Erstellen"
  - "Anwendungsentwicklung [Office-Entwicklung in Visual Studio], Debuggen"
  - "Office-Projektmappen [Office-Entwicklung in Visual Studio], Debuggen"
ms.assetid: c4b79ea8-df70-4a72-b76e-26e337d65727
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Aktualisieren von Office-Projektmappen
  Im Allgemeinen ist das Erstellen und Debuggen von Office\-Projekten mit dem Erstellen und Debuggen von anderen Projekttypen in Visual Studio identisch, z. B. von Windows Forms. Die vorhandenen Unterschiede werden in diesen Themen des Abschnitts erläutert. Weitere allgemeine Informationen zum Erstellen von Anwendungen finden Sie unter [Anwendungen in Visual Studio erstellen](../ide/compiling-and-building-in-visual-studio.md).  
  
## Projektausgabe für Office\-Projekte  
 Der Ausgabeort für Office\-Projekte ist „*Projektname*\\bin\\release“ oder „*Projektname*\\bin\\debug“. Sie können die Erstellung nicht in einem Bereitstellungsverzeichnis vornehmen.  
  
### Projekte auf Dokumentebene  
 Wenn Sie ein Projekt auf Dokumentebene erstellen, sind die folgenden Elemente in der Projektausgabe enthalten:  
  
-   Eine Kopie des Projektdokuments.  
  
-   Die Projektassembly und alle referenzierten Assemblys, deren **Lokale Kopie**\-Eigenschaft auf **true** festgelegt ist.  
  
-   Das Anwendungsmanifest, das die Dateierweiterung „.manifest“ aufweist. Weitere Informationen finden Sie unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
-   Das Bereitstellungsmanifest, das die Dateierweiterung „.vsto“ aufweist. Weitere Informationen finden Sie unter [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md).  
  
-   Eine Programmdatenbankdatei \(PDB\).  
  
> [!NOTE]  
>  Wenn Sie eine Projektmappe auf Dokumentebene an einem Remotespeicherort anstatt auf dem lokalen Computer erstellen, fügen Sie den vollqualifizierten Pfad zur Liste vertrauenswürdiger Speicherorte im Vertrauensstellungscenter der Anwendung hinzu. Weitere Informationen finden Sie im Abschnitt „Gewähren von Vertrauenswürdigkeit für Dokumente“ in [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md).  
  
### Projekte auf Anwendungsebene  
 Wenn Sie ein VSTO Add\-In\-Projekt erstellen, sind die folgenden Elemente in der Projektausgabe enthalten:  
  
-   Die Projektassembly und alle referenzierten Assemblys, deren **Lokale Kopie**\-Eigenschaft auf **true** festgelegt ist.  
  
-   Das Anwendungsmanifest, das die Dateierweiterung „.manifest“ aufweist. Weitere Informationen finden Sie unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
-   Das Bereitstellungsmanifest, das die Dateierweiterung „.vsto“ aufweist. Weitere Informationen finden Sie unter [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md).  
  
-   Eine Programmdatenbankdatei \(PDB\) für die Projektassembly.  
  
 Der Buildprozess für VSTO\-Add\-In\-Projekte erstellt auch einen Satz von Registrierungseinträgen auf dem Entwicklungscomputer, die zum Laden des VSTO\-Add\-Ins erforderlich sind. Weitere Informationen finden Sie unter [Registrierungseinträge für VSTO-Add-Ins](../vsto/registry-entries-for-vsto-add-ins.md).  
  
 Wenn Sie ein VSTO\-Add\-In\-Projekt für Outlook erstellen, das Formularbereiche enthält, werden die folgenden Informationen vom Buildprozess zur Registrierung hinzugefügt:  
  
-   Einen Schlüssel für jede Nachrichtenklasse, die mindestens einem Formularbereich zugeordnet ist.  
  
-   Einen Eintrag für jeden Formularbereich und einen zugeordneten Wert, der den Namen des Outlook VSTO\-Add\-Ins darstellt.  
  
 Outlook benötigt diese Informationen zum Laden der Formularbereiche.  
  
## Assemblys, auf die verwiesen wird  
 Sie können aus Ihrem Projekt „Erstellen von Office\-Projektmappen“ auf Assemblys verweisen \(einschließlich Klassenbibliotheksprojekte\). Jede referenzierte Assembly enthält eine Eigenschaft namens **Lokale Kopie**.**Lokale Kopie** gibt an, ob die Assembly in das Ausgabeverzeichnis kopiert wird. In der Standardeinstellung ist die Eigenschaft auf **true** festgelegt. Jede referenzierte Assembly, bei der **Lokale Kopie** auf **true** festgelegt ist, wird in das Ausgabeverzeichnis kopiert.  
  
## Sicherheit während des Buildprozesses  
 Visual Studio konfiguriert automatisch die Sicherheitseinstellungen auf dem Entwicklungscomputer, um während des Buildprozesses der Projektmappe Vertrauenswürdigkeit zu gewähren. Dadurch kann die Projektmappe beim Debuggen ausgeführt werden.  
  
 Office\-Projekte verwenden Zertifikate, um den Herausgeber zu überprüfen. Visual Studio erstellt automatisch ein temporäres Zertifikat zur Identifizierung von Office\-Projektmappen und konfiguriert den Entwicklungscomputer, damit dem temporären Zertifikat vertraut wird.  
  
 Weitere Informationen finden Sie unter [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md).  
  
### Netzwerkprojekte  
 Wenn sich der Speicherort der Assembly oder des Dokuments auf einer Netzwerkfreigabe befindet, ist die Aktualisierung der lokalen Sicherheitsrichtlinie \(auf Benutzerebene\) nicht ausreichend, um die Ausführung der Projektmappe zu gestatten. Ein Administrator muss Assemblys und Dokumenten, die sich auf einer Netzwerkfreigabe befinden, volle Vertrauenswürdigkeit auf Computerebene gewähren, bevor die Projektmappe ausgeführt werden kann. Weitere Informationen zum Festlegen der Sicherheitsrichtlinie finden Sie unter [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md).  
  
 Für Projekte auf Dokumentebene müssen Sie außerdem den vollqualifizierten Speicherort des Dokuments zur Office\-Liste vertrauenswürdiger Ordner hinzufügen. Weitere Informationen finden Sie unter [Gewähren von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md).  
  
## Ändern der Zielplattform  
 Standardmäßig ist die Zielplattform für Office\-Projekte **Beliebige CPU**. In der Regel sollten Sie diese Einstellung nicht ändern. Office\-Projektmappen, die mit der Zielplattformeinstellung **Beliebige CPU** erstellt werden, werden in 32\-Bit\- und 64\-Bit\-Versionen von Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] oder [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] ausgeführt.  
  
 Sie sollten die Zielplattform nur auf x64 festlegen, wenn Sie eine Projektmappe erstellen, die nur in 64\-Bit\-Versionen von Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] oder [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] ausgeführt wird, und die Projektmappe systemeigene 64\-Bit\-APIs aufruft. Weitere Informationen zum Ändern der Zielplattformeinstellung finden Sie unter [NIB: Gewusst wie: Optimieren einer Anwendung für einen bestimmten CPU\-Typ](http://msdn.microsoft.com/de-de/294a75d2-4279-4b72-8298-2bea05be907a).  
  
 Wenn Sie für die Zielplattform x64 festlegen, kann die Projektmappe nicht in 32\-Bit\-Versionen von Windows oder Office ausgeführt werden. Die x64\-Zielplattform erfordert, dass die Projektmappe in einem 64\-Bit\-Prozess ausgeführt wird.  
  
## Verwenden des Befehls „Bereinigen“  
 Um die erstellten Projektdateien vom Entwicklungscomputer zu entfernen, können Sie den Befehl **Bereinigen** aus dem Menü **Erstellen** in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verwenden. Der Befehl **Bereinigen** löscht alle Dateien im Ausgabespeicherort des Builds. Für Projekte auf Anwendungsebene entfernt der Befehl **Bereinigen** auch die vom Buildprozess erstellten Registrierungseinträge.  
  
## Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|------------------|  
|[Debuggen von Office-Projekten](../vsto/debugging-office-projects.md)|Beschreibt Probleme beim Debuggen von Office\-Projekten.|  
|[Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokumentebene für Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Veranschaulicht, wie Sie eine Standardanpassung auf Dokumentebene für Excel erstellen.|  
|[Gewusst wie: Erneutes Aktivieren eines VSTO-Add-Ins, das deaktiviert wurde](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|Beschreibt der erneute Aktivieren eines zuvor hart oder weich deaktivierten VSTO\-Add\-Ins.|  
|[Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)|Enthält Links zu Informationen über das Erstellen von Office\-Projektmappen und über die Aufgabe, die Assemblys dabei zukommt.|  
  
  