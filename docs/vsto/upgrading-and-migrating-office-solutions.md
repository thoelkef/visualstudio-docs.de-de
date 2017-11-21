---
title: Aktualisieren und Migrieren von Office-Projektmappen | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], upgrading
- Office projects [Office development in Visual Studio], upgrading
- upgrading applications [Office development in Visual Studio]
- upgrading Office solutions in Visual Studio
- migrating Office solutions in Visual Studio
ms.assetid: cc60cdcb-593d-498a-8358-f1f3ac673fe1
caps.latest.revision: "105"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8189032a38aba69b63cb96f824c973b0d41a1aad
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="upgrading-and-migrating-office-solutions"></a>Aktualisieren und Migrieren von Office-Projektmappen
  Wenn Sie über ein Microsoft Office-Projekt verfügen, das in einer früheren Version von Visual Studio erstellt wurde, müssen Sie das Projekt aktualisieren, um es in der aktuellen Version von Visual Studio verwenden zu können. Um ein Microsoft Office-Projekt zu aktualisieren, öffnen Sie es in einer Version von Visual Studio, die die Microsoft Office-Entwicklertools umfasst. Weitere Informationen zu den Versionen von Visual Studio, die die Microsoft Office-Entwicklertools umfassen, finden Sie unter [Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
> [!NOTE]  
>  Bei der Entwicklung von Lösungen, die über die Office-Erfahrungen erweitern "interested" [mehrere Plattformen](https://dev.office.com/add-in-availability)? Sehen Sie sich die neue [Office-Add-ins Modell](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office-Add-ins haben einen geringen Ressourcenbedarf im Vergleich zu VSTO-add-ins und Lösungen, und Sie können sie mithilfe von fast allen Web-Technologien, wie HTML5, JavaScript, CSS3 und XML-Programmierung erstellen.  
  
> [!NOTE]  
>  Von Visual Studio können keine InfoPath-Formularvorlagenprojekte aktualisiert werden, die mit früheren Versionen von Visual Studio erstellt wurden. Diese Projekttypen werden in der aktuellen Version von Visual Studio nicht unterstützt.  
  
## <a name="changes-to-upgraded-projects"></a>Änderungen an aktualisierten Projekten  
 Wenn Sie ein Microsoft Office-Projekt aktualisieren, ändert Visual Studio das Projekt so, dass die folgenden Elemente als Ziel verwendet werden:  
  
-   Visual Studio 2010-Tools für Office-Laufzeit. Weitere Informationen finden Sie unter [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
-   Die aktuellen Assemblyverweise.  
  
-   Eine Version von .NET Framework, die vom Projekttyp unterstützt wird (nur bei einem Upgrade auf Visual Studio 2013).  
  
-   Eine Version von Microsoft Office, die vom Projekttyp unterstützt wird (nur bei einem Upgrade auf Visual Studio 2013).  
  
## <a name="assembly-references"></a>Assemblyverweise  
 Die folgenden Assemblyverweise im Projekt werden aktualisiert:  
  
-   Primäre Interop-Assemblys für Microsoft Office (PIAS).  
  
-   Assemblys in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Weitere Informationen zu diesen Assemblys finden Sie unter [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
-   Neue oder aktualisierte Versionen abhängiger Assemblys.  
  
## <a name="targeted-net-framework"></a>Als Ziel festgelegte .NET Framework-Version  
 Wenn Sie ein Upgrade eines Projekts auf Visual Studio 2013 ausführen, ändert Visual Studio das Projekt für die Verwendung von [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] oder [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]als Zielversion. Die vom Projekt als Ziel verwendete Version von .NET Framework hängt davon ab, welche Version von Office auf dem Computer installiert ist. Wenn nur [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] installiert ist, ändert Visual Studio das Projekt für die Verwendung von [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]als Ziel. Andernfalls ändert Visual Studio das Projekt für die Verwendung von [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]als Ziel.  
  
> [!NOTE]  
>  Unter Umständen sind einige zusätzliche Schritte erforderlich, um eine neu zugewiesene Lösung auf Entwicklungs- und Endbenutzercomputern auszuführen. Das Projekt wird nicht mehr kompiliert, wenn darin bestimmte Funktionen verwendet werden. Weitere Informationen finden Sie unter [Migrieren von Office-Projektmappen zu .NET Framework 4 oder höher](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
 Wenn Sie in einem Office-Projekt [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher als Zielversion festlegen, können Sie einige Features verwenden, die nicht verfügbar sind, wenn .NET Framework 3.5 als Zielversion festgelegt wird. Weitere Informationen finden Sie unter [Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md).  
  
## <a name="targeted-office-application"></a>Als Ziel festgelegte Office-Anwendung  
 Wenn Sie ein Upgrade eines Office-Projekts auf Visual Studio 2013 ausführen, ändert Visual Studio das Projekt so, dass eine Version von Microsoft Office als Zielversion verwendet wird, die durch den Projekttyp unterstützt wird, z. B. ein Anpassungsprojekt auf Dokumentebene oder ein VSTO-Add-In-Projekt.  
  
 Office-Projekte in Visual Studio 2015 können nur [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] und [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] als Zielanwendung verwenden. Visual Studio ändert das Projekt so, dass die aktuellste Version von Office als Zielversion verwendet wird, die Sie installiert haben. Wenn keine dieser Versionen von Office installiert ist, aktualisiert Visual Studio das Projekt nicht.  
  
> [!NOTE]  
>  Wenn Sie ein VSTO-Add-in-Projekt Ziel aktualisieren [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] oder höher, stellen Sie sicher, dass die `ThisAddIn_Startup` -Ereignishandler des VSTO-Add-Ins keinen Code, der ein Dokument in der Anwendung zugreift enthält. Weitere Informationen finden Sie unter [Accessing a Document When the Office Application Starts](../vsto/programming-vsto-add-ins.md#AccessingDocuments).  
  
 Bei Anpassungen auf Dokumentebene konvertiert [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] Dokumente mit Binärformat in einem Projekt, z. B. Dokumente mit XLS- oder DOC-Erweiterung, in das Office Open XML-Format. Weitere Informationen zu Open XML finden Sie unter [Einführung in neue Dateinamenerweiterungen und Microsoft Office Open XML-Formate](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1).  
  
> [!NOTE]  
>  Smarttags sind in Excel 2010 und Word 2010 veraltet. Wenn Ihre Projektmappe Smarttags verwendet, müssen Sie diese entfernen, bevor Sie sie in Visual Studio 2013 oder Visual Studio 2015 testen und debuggen können.  
  
## <a name="upgrading-microsoft-office-2003-projects"></a>Aktualisieren von Microsoft Office 2003-Projekten  
 Für die Aktualisierung von Anpassungen auf Dokumentebene und VSTO-Add-Ins für Microsoft Office 2003 gelten einige weitere Überlegungen.  
  
### <a name="document-level-projects"></a>Projekte auf Dokumentebene  
 Falls das Dokument im Projekt Windows Forms-Steuerelemente enthält, müssen Sie die Visual Studio 2005-Tools für Office Second Edition-Laufzeit installieren, bevor Sie das Projekt aktualisieren. Wenn diese Version der Laufzeit vor dem Aktualisieren des Projekts nicht auf dem Entwicklungscomputer installiert wird, können im aktualisierten Projekt Kompilier- oder Laufzeitfehler auftreten. Nachdem Sie das Projekt aktualisiert haben, können Sie die Visual Studio 2005-Tools für Office Second Edition-Laufzeit vom Entwicklungscomputer deinstallieren, wenn sie nicht von anderen Office-Projektmappen verwendet wird. Diese Version der Laufzeit steht im Microsoft Download Center unter [Microsoft Visual Studio 2005-Tools für Office Second Edition-Laufzeit (VSTO 2005 SE) (x86)](http://go.microsoft.com/fwlink/?linkid=49612)als verteilbares Paket zur Verfügung.  
  
### <a name="vsto-add-in-projects"></a>VSTO-Add-In-Projekte  
 Wenn die Projektmappendatei für das ursprüngliche Projekt ein Setup- oder InstallShield Limited Edition-Projekt enthielt, das dafür konfiguriert war, das VSTO-Add-In zu installieren, aktualisiert Visual Studio das Projekt, nimmt jedoch keine weiteren Änderungen am Projekt vor. Wenn Sie das VSTO-Add-In weiterhin mit einer Windows Installer-Datei bereitstellen möchten, muss das Setup- oder InstallShield Limited Edition-Projekt so geändert werden, dass neue erforderliche Komponenten wie [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], Visual Studio 2010 Tools für Office-Laufzeit und optional die primären Interopassemblys, auf die durch das VSTO-Add-In verwiesen wird, installiert werden. Weitere Informationen finden Sie unter [Deploying an Office Solution by Using Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
 Wenn Sie das VSTO-Add-In mit ClickOnce bereitstellen möchten, können Sie das Setup- oder das InstallShield Limited- Edition-Projekt vollständig löschen. Weitere Informationen zum Bereitstellen von VSTO-Add-ins mithilfe von ClickOnce finden Sie unter [Bereitstellen einer Office-Lösung](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Aktualisieren von Office-Projektmappen](http://msdn.microsoft.com/en-us/a269e539-b717-4680-a568-2152b070347e)   
 [Migrating Office Solutions to the .NET Framework 4 or later](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Projektupgrade, Dialogfeld „Optionen“](../vsto/project-upgrade-options-dialog-box.md)  
  
  