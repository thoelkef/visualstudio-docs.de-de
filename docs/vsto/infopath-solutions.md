---
title: InfoPath-Projektmappen
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], InfoPath
- templates [Office development in Visual Studio], InfoPath
- InfoPath [Office development in Visual Studio]
- Office development in Visual Studio, InfoPath solutions
- projects [Office development in Visual Studio], InfoPath
- Office solutions [Office development in Visual Studio], InfoPath
- Office projects [Office development in Visual Studio], InfoPath
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 09880992ff2e0d85e4706fb65753a31e49713e1d
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54862732"
---
# <a name="infopath-solutions"></a>InfoPath-Projektmappen
  In Visual Studio werden Projektvorlagen bereitgestellt, die Sie zum Erstellen von VSTO-Add-Ins für Microsoft Office InfoPath 2013 und InfoPath 2010 verwenden können. InfoPath ist in Office 2016 nicht verfügbar.  
  
> [!NOTE]  
>  Sie können trotzdem ein VSTO-Add-in für InfoPath erstellen, wenn Sie Office 2016 installiert haben. Installieren Sie InfoPath 2013 oder Office 2013 einfach zusätzlich zu Office 2016.  
  
 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]  
  
> [!NOTE]  
>  Möchten Sie bei der Entwicklung von Lösungen, die über die Office-Erfahrungen erweitern [mehrere Plattformen](https://dev.office.com/add-in-availability)? Sehen Sie sich die neue [Office-Add-ins Modell](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office-Add-ins verfügen, einen geringen Ressourcenbedarf im Vergleich zu VSTO-Add-ins und Lösungen, und Sie können sie mithilfe von fast allen Web-Technologien, wie HTML5, JavaScript, CSS3 und XML-Programmierung erstellen.  
  
 VSTO-Add-Ins für InfoPath ähneln VSTO-Add-Ins für andere Microsoft Office-Anwendungen. Diese Typen von Projektmappen bestehen aus einer Assembly, die von der Anwendung geladen wird. Endbenutzer können auf die Funktionen dieser Assembly zugreifen, unabhängig davon, welches Formular bzw. welche Formularvorlage geöffnet ist. Weitere Informationen zu VSTO-Add-ins finden Sie unter [erste Schritte zum Programmieren von VSTO-Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) und [Architecture of VSTO-Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
> [!NOTE]  
>  Visual Studio 2015 enthält nicht die InfoPath-Formularvorlagenprojekte, die in früheren Versionen von Visual Studio bereitgestellt wurden. Sie können auch Visual Studio 2015 nicht verwenden, um ein in einer früheren Version von Visual Studio erstelltes InfoPath-Formularvorlagenprojekt zu öffnen oder zu bearbeiten. Ein InfoPath-Formularvorlagenprojekt kann jedoch mit Visual Studio Tools for Applications geöffnet und bearbeitet werden. Weitere Informationen finden Sie unter [arbeiten mit VSTO 2008-Projekten in InfoPath 2010.](http://go.microsoft.com/fwlink/?LinkID=218903).  
  
## <a name="automate-infopath-by-using-an-add-in"></a>Automatisieren von InfoPath mithilfe eines Add-Ins  
 Verwenden Sie zum Zugreifen auf das InfoPath-Objektmodell von einem Office VSTO-Add-In aus, das mit Office-Entwicklungstools in Visual Studio erstellt wurde, das `Application` -Feld der `ThisAddIn` -Klasse im Projekt. Das `Application` -Feld gibt ein <xref:Microsoft.Office.Interop.InfoPath.Application> -Objekt zurück, das die aktuelle Instanz von InfoPath darstellt. Weitere Informationen finden Sie unter [Programm VSTO-Add-ins](../vsto/programming-vsto-add-ins.md).  
  
 Wenn Sie das InfoPath-Objektmodell aus einem VSTO-Add-in aufrufen, verwenden Sie Typen, die in der primären Interopassembly für InfoPath bereitgestellt werden. Die primäre Interopassembly dient als Brücke zwischen verwaltetem Code im VSTO-Add-In und dem COM-Objektmodell in InfoPath. Alle Typen in der primären Interopassembly für InfoPath werden im <xref:Microsoft.Office.Interop.InfoPath> -Namespace definiert. Weitere Informationen zu der primären Interopassembly für InfoPath finden Sie unter [über die Microsoft Office InfoPath primäre interop-Assembly](https://msdn.microsoft.com/1b3ae03c-6951-49e4-a489-4712d3f7ba72). Weitere Informationen zu primären Interopassemblys im Allgemeinen finden Sie unter [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) und [primären Interopassemblys für Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="customize-the-user-interface-of-infopath-by-using-an-add-in"></a>Anpassen der Benutzeroberfläche von InfoPath mithilfe eines Add-Ins  
 Wenn Sie ein VSTO-Add-in für InfoPath erstellen, müssen Sie mehrere verschiedene Optionen für die UI-Anpassung aus. In der folgenden Tabelle werden einige dieser Optionen aufgeführt.  
  
|Aufgabe|Weitere Informationen|  
|----------|--------------------------|  
|Erstellen eines benutzerdefinierten Aufgabenbereichs|[Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)|  
|Hinzufügen benutzerdefinierter Registerkarten zum Menüband in InfoPath|[Anpassen eines Menübands für InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|  
  
 Weitere Informationen zum Anpassen der Benutzeroberfläche von InfoPath und anderen Microsoft Office-Anwendungen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Informationen zu der primären Interopassembly für Microsoft Office InfoPath](https://msdn.microsoft.com/1b3ae03c-6951-49e4-a489-4712d3f7ba72)   
 [Erste Schritte zum Programmieren von VSTO-Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)   
 [Schreiben Sie Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)   
 [Primäre Interopassemblys für Office](../vsto/office-primary-interop-assemblies.md)   
 [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)   
 [InfoPath 2010 unter Office-Entwicklung](http://go.microsoft.com/fwlink/?LinkId=199012)  
