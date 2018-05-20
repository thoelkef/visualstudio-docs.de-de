---
title: Entwerfen und Erstellen von Office-Projektmappen
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], creating
- Office development in Visual Studio, creating solutions
- solutions [Office development in Visual Studio], creating
- Office project types in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 453628910bcafac3882345d63442a6321b557aab
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="design-and-create-office-solutions"></a>Entwerfen und Erstellen von Office-Projektmappen
  Visual Studio stellt Projektvorlagen bereit, mit denen Sie mehrere unterschiedliche Typen von Office-Projektmappen erstellen können. In diesem Abschnitt der Dokumentation werden die Projektvorlagen beschrieben und Anweisungen zum Erstellen von Office-Projekten bereitgestellt. Informationen zum Implementieren von Code- und Benutzeroberflächenanpassungen nach dem Sie das Projekt erstellt haben, finden Sie unter [Entwickeln von Office-Projektmappen](../vsto/developing-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  Bei der Entwicklung von Lösungen, die über die Office-Erfahrungen erweitern "interested" [mehrere Plattformen](https://dev.office.com/add-in-availability)? Sehen Sie sich die neue [Office-Add-ins Modell](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office-Add-ins haben einen geringen Ressourcenbedarf im Vergleich zu VSTO-Add-ins und Lösungen, und Sie können sie mithilfe von fast allen Web-Technologien, wie HTML5, JavaScript, CSS3 und XML-Programmierung erstellen.  
  
## <a name="create-office-projects"></a>Erstellen von Office-Projekten  
 Bevor Sie beginnen, sollten Sie die Anforderungen bestimmen und den am besten geeigneten Lösungstyp festlegen. Wenn die Office-Projektmappe z. B. bei jeder Verwendung der Anwendung ausgeführt werden muss, ist ein VSTO-Add-In die beste Lösung für Ihre Anforderungen. Wenn der Code fest in ein einzelnes Dokument integriert ist, erstellen Sie eine Anpassung auf Dokumentebene. Diese Projekttypen sind als Visual Studio-Projektvorlagen verfügbar. Weitere Informationen zu den Office-Projektvorlagen, die in Visual Studio enthalten sind, finden Sie unter [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md). Weitere Informationen zum Erstellen von Office-Projekten finden Sie unter [Vorgehensweise: Erstellen von Office-Projekte in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Office-Projekte enthalten Funktionen und Projektelemente, die sich von anderen Projekttypen in Visual Studio unterscheiden. Wenn Sie z. B. ein Projekt auf Dokumentebene erstellen, kann das Dokument oder die Arbeitsmappe im Projekt in Visual Studio geöffnet und bearbeitet werden. Weitere Informationen finden Sie unter [Office-Projekte in Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="choose-a-net-framework-version"></a>Wählen Sie eine .NET Framework-version  
 Nachdem Sie den für Ihre Anforderungen am besten geeigneten Projekttyp ausgewählt haben, können Sie festlegen, welche .NET Framework-Version bei der Entwicklung verwendet werden soll. In Office-Projekten können die folgenden .NET Framework-Versionen verwendet werden:  
  
-   [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]  
  
-   [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]  
  
-   [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
  
 Die für das Projekt ausgewählte .NET Framework-Version muss auf Endbenutzercomputern vorhanden sein, um die Projektmappe ausführen zu können. Wenn für das Projekt z. B. [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] als Zielversion festgelegt ist, ist [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] auf Endbenutzercomputern erforderlich. In diesem Beispiel wird die Projektmappe nicht ausgeführt, wenn nur .NET Framework 3.5 auf Endbenutzercomputern installiert ist.  
  
 Wenn Sie ein VSTO-Add-In-Projekt migrieren, das .NET Framework 3.5 als Ziel verwendet, ändert Visual Studio das Zielframework des Projekts in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher, je nach installierter Office-Version.  
  
 Nachdem das Zielframework von Visual Studio geändert wurde, müssen Sie jedoch möglicherweise einen Teil des Codes im Projekt ändern, wenn es bestimmte Funktionen verwendet. Weitere Informationen zum Ändern des Zielframeworks finden Sie unter [wie: eine Version von .NET Framework als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Weitere Informationen zu Änderungen, die Sie möglicherweise im Projekt erstellen, finden Sie unter [Migrieren von Office-Projektmappen zu .NET Framework 4 oder höher](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
 Wenn das Ziel-.NET Framework des Projekts von Visual Studio geändert, und Sie ClickOnce zum Bereitstellen Ihrer Lösung verwenden, stellen Sie sicher, dass Sie auch wählen Sie die entsprechende Version von .NET Framework in die **Voraussetzungen** (Dialogfeld). Diese Auswahl wird nicht automatisch geändert, wenn Sie das Zielframework für das Projekt ändern. Weitere Informationen finden Sie unter [Vorgehensweise: Installieren der erforderlichen Komponenten auf Endbenutzercomputern zum Ausführen von Office-Projektmappen](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
> [!NOTE]  
>  Sie können .NET Framework 3.5 oder frühere Versionen in Office-Projekten, die Sie mit [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] erstellen, nicht als Ziel verwenden. Office-Projekte, die Sie mit [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] erstellen, erfordern Funktionen, die anfänglich in [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] eingeführt wurden.  
  
### <a name="understand-when-the-office-pias-are-required-on-end-user-computers"></a>Zu verstehen, wenn die Office-PIAs auf Endbenutzercomputern erforderlich sind  
 Standardmäßig Office primary Interop-Assemblys (PIAs) müssen nicht auf Endbenutzercomputern installiert sein, wenn die **Interoptypen** jedes Office PIA-Verweises im Projekt ist-Eigenschaftensatz auf **"true"**, welche ist der Standardwert. In diesem Szenario werden die in der Projektmappe für die PIA-Typen verwendeten Typinformationen beim Erstellen des Projekts in die Projektmappenassembly eingebettet. Zur Laufzeit wird die eingebetteten Typinformationen statt der PIAs verwendet, um COM-basierten Objektmodell der Office-Anwendung aufzurufen. Weitere Informationen dazu, wie die Typen aus PIAs in Ihre Projektmappe eingebettet sind, finden Sie unter [Typäquivalenz und eingebettete Interop-Typen](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types).  
  
 Wenn die **Interoptypen** jedes Office PIA-Verweises im Projekt ist-Eigenschaftensatz auf **"false"**, Office-PIAs müssen installiert und registriert, die im globalen Assemblycache auf jedem Endbenutzercomputer, führt Sie die Projektmappe ein. In den meisten Fällen werden die PIAs standardmäßig mit Office installiert, Sie können die verteilbare PIA jedoch auch als erforderliche Komponente für die Lösung einschließen. Weitere Informationen finden Sie unter [erforderliche Komponenten für Office-Projektmappen für die Bereitstellung](http://msdn.microsoft.com/en-us/9f672809-43a3-40a1-9057-397ce3b5126e).  
  
### <a name="understand-the-client-profile"></a>Verstehen der Clientprofil  
 .NET Framework Client Profile ist eine Teilmenge der Vollversion von .NET Framework. Sie können .NET Framework Client Profile verwenden, wenn nur die Clientfunktionen in .NET Framework verwendet werden müssen und die schnellstmögliche Bereitstellung für die Office-Lösung angegeben werden soll. Weitere Informationen finden Sie unter [.NET Framework-Clientprofil](/dotnet/framework/deployment/client-profile).  
  
 Wenn Sie ein Office-Projekt erstellen, das auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] abzielt, wird [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] standardmäßig als Ziel verwendet. Wenn Sie ein Projekt für das vollständige [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] entwickeln möchten, müssen Sie diese Option festlegen, nachdem das Projekt erstellt wurde. Weitere Informationen finden Sie unter [Vorgehensweise: .NET Framework-Version als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
## <a name="create-solutions-for-the-64-bit-edition-of-microsoft-office"></a>Erstellen Sie für die 64-Bit-Edition von Microsoft Office-Projektmappen  
 Microsoft Office ist in 64-Bit- und 32-Bit-Editionen verfügbar. Zum Erstellen von Office-Projektmappen, die in beiden Edition ausgeführt werden kann, muss die zielplattformeinstellung für das Projekt festgelegt werden **Any CPU**. Dies ist der Standardwert für Office-Projekte. Weitere Informationen finden Sie unter [Erstellen von Office-Projektmappen](../vsto/building-office-solutions.md).  
  
 Es gibt separate 64-Bit- und 32-Bit-Versionen von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], die von den 64-Bit- und 32-Bit-Editionen von Microsoft Office verwendet werden. Weitere Informationen finden Sie unter [Visual Studio-Tools für Office-laufzeitübersicht](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="assemblies-in-office-solutions"></a>Assemblys in Office-Projektmappen  
 Wenn Sie mit den Office-Entwicklungstools in Visual Studio ein Office-Projekt erstellen, wird der Code, den Sie schreiben, schließlich in eine Assembly kompiliert. Die Assembly wird meist auf einem freigegebenen Server oder in einem Verzeichnis auf dem Clientcomputer bereitgestellt.  
  
 Assemblys in Office-Projektmappen werden von einer Office-Anwendung geladen. Nach dem Laden der Assembly kann Code in der Assembly auf Ereignisse reagieren, die in der Anwendung ausgelöst werden, z. B. wenn ein Benutzer auf ein Menüelement klickt. Der Code in der Assembly kann auch einen Aufruf an das Objektmodell ausführen, um die Anwendung zu automatisieren und zu erweitern, und der Code kann jede der Klassen in [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] verwenden. Weitere Informationen finden Sie unter [Architektur von Anpassungen auf Dokumentebene](../vsto/architecture-of-document-level-customizations.md) und [Architektur von VSTO-Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
 Office-Lösungen identifizieren die Assembly mithilfe von Bereitstellungsmanifesten und Anwendungsmanifesten. Die Manifeste enthalten Informationen über Name, Version und Speicherort der Assembly, sodass die Anwendung die richtige Assembly suchen, eine Verbindung mit dieser herstellen und diese ausführen kann. Weitere Informationen finden Sie unter [-Anwendungsmanifest und-Bereitstellungsmanifest in Office-Projektmappen](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
 Projekte auf Dokumentebene enthalten zusätzlich zu einer Assembly ein Dokument. Das Dokument bildet das Front-End der Anwendung, in dem alle Benutzerinteraktionen stattfinden. Jedes Dokument kann nur mit einer Hauptprojektassembly verknüpft sein, es können jedoch mehrere Dokumente auf dieselbe Assembly verweisen.  
  
 Assemblys in Projekten auf Dokumentebene sind nicht im Dokument eingebettet, sondern werden an anderer Stelle gespeichert und durch das Anwendungsmanifest des Dokuments identifiziert.  
  
## <a name="security-considerations-for-assemblies"></a>Sicherheitsüberlegungen bei Assemblys  
 Damit eine Office-Lösung auf einem Computer ausgeführt werden kann, müssen die von der Lösung verwendeten Assemblys als vertrauenswürdig gelten, um ausgeführt zu werden. Weitere Informationen zur Sicherheit finden Sie unter [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md).  
  
 Standardmäßig gelten die Projektmappenassembly und alle Assemblys, auf die verwiesen wird und die sich im Ausgabeordner des Projekts befinden, als vertrauenswürdig, um beim Erstellen des Projekts auf dem Entwicklungscomputer ausgeführt zu werden. Weitere Informationen finden Sie unter [Erstellen von Office-Projektmappen](../vsto/building-office-solutions.md).  
  
 Aus Sicherheitsgründen empfiehlt es sich, Projekte auf dem lokalen Computer und nicht in einem freigegebenen Speicherort zu erstellen. Weitere Informationen finden Sie unter [gemeinsame Entwicklung von Office-Projektmappen](../vsto/collaborative-development-of-office-solutions.md).  
  
## <a name="referenced-assemblies"></a>Assemblys, auf die verwiesen wird  
 Eine Assembly kann auf andere Assemblys verweisen, die in den Verweisen des Projekts aufgelistet sind. Eine Assembly in einem Projekt auf Dokumentebene kann jedoch auf keine andere Assembly in einem Projekt auf Dokumentebene verweisen.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)   
 [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Office-Projekte in Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md)   
 [Eigenschaften in Office-Projekten](../vsto/properties-in-office-projects.md)   
 [Projektmappen in verschiedenen Versionen von Microsoft Office ausführen.](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)   
 [Vorgehensweise: Ziel Office-Anwendungen durch primäre Interopassemblys](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Anwendungs- und Bereitstellungsmanifeste in Office-Projektmappen](../vsto/application-and-deployment-manifests-in-office-solutions.md)   
 [Vorgehensweise: Einrichten von Konfigurationsinformationen für eine Office-Projektmappe](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)   
 [Verwenden von Office-Funktionen in Visual Studio](../vsto/using-office-functionality-inside-of-visual-studio.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)   
 [Häufige Aufgaben bei der Programmierung mit Office](../vsto/common-tasks-in-office-programming.md)   
 [Entwickeln von Office-Projektmappen](../vsto/developing-office-solutions.md)   
 [Architektur von Office-Projektmappen in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  