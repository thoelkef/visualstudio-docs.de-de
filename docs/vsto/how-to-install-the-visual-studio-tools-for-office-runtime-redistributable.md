---
title: 'Vorgehensweise: Installieren der Visual Studio-Tools für Office-Laufzeit'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 83bc53dec2c4085b59a07ddc4694ff184b9e75a7
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648495"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Vorgehensweise: Installieren der Visual Studio-Tools für Office-Laufzeit
  Visual Studio 2010-Tools für Office-Laufzeit muss installiert sein, auf jedem Computer, die Lösungen ausgeführt, die erstellt werden wird, indem Sie mit der Microsoft Office Developer Tools in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Die Laufzeit wird automatisch installiert, wenn Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und Microsoft Office installieren. Weitere Informationen finden Sie unter [Visual Studio-Tools für Office Runtime Installation Scenarios](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
 Sie müssen möglicherweise die Anweisungen zur manuellen Installation weiter unten in den folgenden Situationen befolgen:  
  
-   Sie müssen [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] auf einem Server installieren. Sie möchten z. B. die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>-Klasse verwenden, um Lösungen auf Dokumentebene auf einem Server zu verwalten.  
  
-   Sie müssen die Laufzeit auf einem Computer installieren, auf dem bereits alle anderen erforderlichen Komponenten für Office-Lösungen installiert wurden.  
  
    > [!NOTE]  
    >  Sie müssen auf dem Entwicklungscomputer über Administratorrechte verfügen, um .NET Framework und [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zu installieren.  
  
## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>So installieren Sie Visual Studio Tools for Office Runtime  
  
1.  Installieren Sie [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher.  
  
    -   Zum Herunterladen der [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], finden Sie unter [Microsoft .NET Framework 4 (Webinstaller)](http://go.microsoft.com/fwlink/?LinkId=178957).  
  
    -   Zum Herunterladen der [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)], finden Sie unter [Microsoft .NET Framework 4 Client Profile (Webinstaller)](http://go.microsoft.com/fwlink/?LinkId=178958).  
  
    -   Zum Herunterladen der [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], finden Sie unter [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).  
  
2.  Führen Sie *vstor_redist.exe* zum Installieren der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
     Sie können diese Setupdateien unter [Visual Studio 2010-Tools für Office-Laufzeit](http://go.microsoft.com/fwlink/?LinkId=140384). Die erforderlichen Komponenten für [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] stimmen mit denen für .NET Framework überein.  
  
     Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]enthält Sprachpakete. Wenn Sie für Windows andere Spracheinstellungen als Englisch festgelegt haben, können Sie Laufzeitmeldungen in der Sprache anzeigen, die Sie für Windows verwenden. Wenn Endbenutzer [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] installieren und dann die Projektmappen auf Windows-Installationen ausführen, die andere Spracheinstellungen als Englisch verwenden, werden Laufzeitmeldungen entsprechend in derselben Sprache wie Windows angezeigt. In einigen Fällen benötigen Sie möglicherweise zusätzliche Sprachpakete. Beispielsweise können Sie zusätzliche Sprachpakete benötigen, wenn Ihre Kopie von Windows wird mehr als eine Spracheinstellung verwendet oder Sie zu einer anderen Sprache wechseln, nachdem Sie bereits installiert haben die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Sie finden die Sprachpakete an [Microsoft Visual Studio 2010-Tools für Microsoft Office System (Laufzeitversion 4.0) Language Pack](http://go.microsoft.com/fwlink/?LinkId=140386).  
  
## <a name="see-also"></a>Siehe auch  
 [Erste Schritte &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen](../vsto/configuring-a-computer-to-develop-office-solutions.md)   
 [Vorgehensweise: Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [Vorgehensweise: Installieren von primären Interopassemblys für Office](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)  
  
  