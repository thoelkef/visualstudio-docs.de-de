---
title: Übersicht über das Visio-Objektmodell
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], object model
- object models [Office development in Visual Studio], Office
- object models [Office development in Visual Studio], Visio
- objects [Office development in Visual Studio], Office object models
- Office object models
- Visio object model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 040144b1e18e216ef8ceadbd218cd42ccf7c40f1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848466"
---
# <a name="visio-object-model-overview"></a>Übersicht über das Visio-Objektmodell
  Zur Entwicklung von Office-Projektmappen für Microsoft Office Visio können Sie mit dem Visio-Objektmodell interagieren. Dieses Objektmodell besteht aus Klassen und Schnittstellen, die in der primären Interopassembly für Visio bereitgestellt und im `Microsoft.Office.Interop.Visio`-Namespace definiert werden.  
  
 Dieses Thema enthält eine kurze Übersicht über das Visio-Objektmodell. Informationen zur Verwendung des Visio-Objektmodells für bestimmte Aufgaben in Office-Projekten finden Sie unter den folgenden Themen:  
  
-   [Arbeiten mit Visio-Dokumenten](../vsto/working-with-visio-documents.md)  
  
-   [Arbeiten mit Visio-shapes](../vsto/working-with-visio-shapes.md)  
  
## <a name="understand-the-visio-object-model"></a>Verstehen von Visio-Objektmodell  
 Visio stellt zahlreiche Objekte bereit, mit denen Sie interagieren können. Diese Objekte werden in einer Hierarchie angeordnet, die eng an die Benutzeroberfläche angelehnt ist. Oben in der Hierarchie befindet sich das [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application) -Objekt. Dieses Objekt stellt die aktuelle Instanz von Visio dar. Die `Microsoft.Office.Interop.Visio.Application` Objekt enthält die `Microsoft.Office.Interop.Visio.Document` und `Microsoft.Office.Interop.Visio.Page` Objekte als auch die `Microsoft.Office.Interop.Visio.Documents` und `Microsoft.Office.Interop.Visio.Pages` Sammlungen. Jedes dieser Objekte bzw. jede dieser Auflistungen verfügt über zahlreiche Methoden und Eigenschaften, auf die Sie zwecks Bearbeitung und Interaktion zugreifen können.  
  
 Weitere Informationen finden Sie in der VBA-Referenzdokumentation für die Objekte [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application), [Microsoft.Office.Interop.Visio.Document](/office/vba/api/Visio.Document)und [Microsoft.Office.Interop.Visio.Page](/office/vba/api/Visio.Page) sowie für die Auflistungen [Microsoft.Office.Interop.Visio.Documents](/office/vba/api/Visio.Documents) und [Microsoft.Office.Interop.Visio.Pages](/office/vba/api/Visio.Pages) .  
  
 In den folgenden Abschnitten werden die Objekte der obersten Ebene und ihre Interaktion miteinander kurz beschrieben. Dazu gehören die folgenden Objekte:  
  
-   Application-Objekt  
  
-   Document-Objekt  
  
-   Page-Objekt  
  
### <a name="application-object"></a>Application-Objekt  
 Die Microsoft.Office.Interop.Visio.Application-Objekt stellt die Visio-Anwendung dar und ist das übergeordnete Element aller anderen Objekte. Seine Elemente gelten normalerweise für Visio als Ganzes. Können Sie die Eigenschaften und Methoden der Microsoft.Office.Interop.Visio.Application und `Microsoft.Office.Interop.Visio.ApplicationSettings` Objekte zum Steuern der Visio-Umgebung.  
  
 In VSTO-Add-in-Projekten können Sie das Microsoft.Office.Interop.Visio.Application Objekt zugreifen, mithilfe der `Application` Feld der `ThisAddIn` Klasse. Weitere Informationen finden Sie unter [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
### <a name="document-object"></a>Document-Objekt  
 Das Microsoft.Office.Interop.Visio.Document-Objekt ist für Visio-Programmierung von zentraler Bedeutung. Es stellt eine Zeichnungs-, Schablonen- oder Vorlagendatei dar. Wenn Sie ein Visio-Dokument öffnen oder ein neues Dokument erstellen, erstellen Sie ein neues Microsoft.Office.Interop.Visio.Document-Objekt, das der Auflistung Microsoft.Office.Interop.Visio.Documents des Objekts Microsoft.Office.Interop.Visio.Application hinzugefügt wird .  
  
 Das Dokument, das den Fokus besitzt, wird als das aktive Dokument bezeichnet. Es wird dargestellt, durch die `Microsoft.Office.Interop.Visio.Application.ActiveDocument` -Eigenschaft des Objekts Microsoft.Office.Interop.Visio.Application.  
  
### <a name="page-object"></a>Page-Objekt  
 Das Objekt Microsoft.Office.Interop.Visio.Page stellt den Zeichnungsbereich einer Vordergrund- oder Hintergrundseite dar. Mithilfe der `Microsoft.Office.Interop.Visio.Page.Background`-Eigenschaft können Sie feststellen, ob es sich bei der Seite um eine Vorder- oder Hintergrundseite handelt.  
  
 Zum Erstellen von Shapes können Sie Methoden wie die `Microsoft.Office.Interop.Visio.Page.DrawSpline`-Methode und die `Microsoft.Office.Interop.Visio.Page.DrawOval`-Methode verwenden. Darüber hinaus können Sie Masters aus Schablonen abrufen und die Shapes mithilfe der `Microsoft.Office.Interop.Visio.Page.Drop`-Methode oder `Microsoft.Office.Interop.Visio.Page.DropMany`-Methode auf einer Seite platzieren.  
  
## <a name="use-the-visio-object-model-documentation"></a>Verwenden der Dokumentation zum Visio-Objektmodell  
 Ausführliche Informationen zum Visio-Objektmodell finden Sie in der VBA-Objektmodellreferenz für Visio. Die VBA-Objektmodellreferenz dokumentiert das Visio-Objektmodell, das für VBA (Visual Basic for Applications) verfügbar gemacht wird. Weitere Informationen finden Sie unter [Visio 2010-Objektmodellreferenz](http://go.microsoft.com/fwlink/?LinkId=199775).  
  
 Alle Objekte und Member in der VBA-Objektmodellreferenz entsprechen Typen und Membern in der primären Interopassembly (PIA) für Visio. Z. B. die `Document` Objekt in der VBA-Objektmodellreferenz entspricht dem Microsoft.Office.Interop.Visio.Document-Typ in der Visio-PIA. Obwohl die VBA-Objektmodellreferenz Codebeispiele für die meisten Eigenschaften, Methoden und Ereignisse enthält, müssen Sie den VBA-Code in dieser Referenz in Visual Basic oder Visual C# übersetzen, wenn Sie ihn in einem mit Visual Studio erstellten Visio VSTO-Add-In-Projekt verwenden möchten.  
  
> [!NOTE]  
>  Derzeit ist keine Referenzdokumentation für die primäre Interopassembly für Visio verfügbar.  
  
 Verwandte Codebeispiele und weitere Tools zum Erstellen von Visio-Projektmappen finden Sie [Visio 2010 Software Development Kits](http://go.microsoft.com/fwlink/?LinkId=196501).  
  
### <a name="additional-types-in-primary-interop-assemblies"></a>Zusätzliche Typen in primären Interopassemblys  
 Primäre Interopassemblys können Typen enthalten, die aufgrund von Unterschieden bei der Implementierung nicht für VBA sichtbar sind. VBA bietet eine Ansicht des Visio-Objektmodells, das nur die Objekte und Member enthält, die Sie direkt verwenden können. Die primären Interopassemblys machen das gleiche Objektmodell verfügbar, enthalten zusätzlich aber weitere Schnittstellen, Klassen und Member, die Objekte im COM-Objektmodell in verwalteten Code übersetzen. Diese zusätzlichen Elemente sollten nicht direkt im Code verwendet werden.  
  
 Weitere Informationen finden Sie unter [Übersicht über Klassen und Schnittstellen in den primären Interopassemblys für Office](http://go.microsoft.com/fwlink/?LinkId=189592) und [primären Interopassemblys für Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Visio-Projektmappen](../vsto/visio-solutions.md)   
 [Arbeiten mit Visio-Dokumenten](../vsto/working-with-visio-documents.md)   
 [Arbeiten mit Visio-shapes](../vsto/working-with-visio-shapes.md)  
