---
title: Erweitern des SharePoint-Projektsystems | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cabb70ba998594d99242696d0f87d60d5eb01226
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766089"
---
# <a name="extend-the-sharepoint-project-system"></a>SharePoint-Projektsystem erweitern
  Sie können SharePoint-Lösungen erstellen, indem Sie mit der eine Reihe von Projektvorlagen und Elementvorlagen in Visual Studio. Diese Vorlagen erfüllen viele Entwicklungsszenarien, aber Sie möglicherweise heraus, dass einige Fälle, in denen diese Funktionalität nicht bereitstellen, die Sie benötigen. In diesen Fällen können Sie die SharePoint-Projektsystem erweitern.  
  
## <a name="overview-of-the-sharepoint-project-system"></a>Übersicht über die SharePoint-Projektsystem
 SharePoint-Projektsystem basiert darauf, dass die grundlegende Komponente des *SharePoint-Projektelemente*. Ein SharePoint-Projektelement stellt eine SharePoint-Anpassung, z. B. einer Listendefinition, Webpart oder Inhaltstyp dar.  
  
 Ein SharePoint-Projekt ist ein Visual Studio-Projekt, das eine oder mehrere SharePoint-Projektelemente enthält. SharePoint-Projekte enthalten auch weitere Komponenten, die definieren, wie Projektelemente in Funktionen und Pakete für die Bereitstellung gruppiert sind.  
  
 Weitere Informationen zum Inhalt der SharePoint-Projektelemente und SharePoint-Projekte finden Sie unter [Erstellen von Elementvorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="how-to-extend-the-sharepoint-project-system"></a>Gewusst wie: Erweitern der SharePoint-Projektsystem
 Sie können SharePoint-Projektsystem erweitern, auf folgende Weise:  
  
-   Definieren Sie eigene SharePoint-Projektelementtypen, und ordnen sie neue Vorlagen oder -Projektvorlagen in Visual Studio. Beispielsweise können Sie einen SharePoint-Projektelementtyp definieren, für das Erstellen einer benutzerdefinierten Aktion oder ein Feld. Weitere Informationen finden Sie unter [Definieren von benutzerdefinierten SharePoint Projektelementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
-   Erweitern Sie SharePoint-Projektelementtypen, die in Visual Studio bereits installiert sind. Sie können z. B. ein Kontextmenüelement hinzufügen, in der ein Projektelement in **Projektmappen-Explorer** und passen Sie das Projektelement aus, wenn ein Entwickler das Menüelement auswählt. Weitere Informationen finden Sie unter [Erweitern von SharePoint-Projektelemente](../sharepoint/extending-sharepoint-project-items.md).  
  
-   Erweitern Sie SharePoint-Projekte. Beispielsweise können Sie Ereignishandler, um bestimmte Aufgaben auszuführen, wenn Elemente hinzugefügt oder aus der SharePoint-Projekte entfernt hinzufügen. Weitere Informationen finden Sie unter [Erweitern von SharePoint-Projekte](../sharepoint/extending-sharepoint-projects.md).  
  
-   Erweitern Sie das Packen und-Bereitstellen Verhalten des SharePoint-Projektelemente und SharePoint-Projekte. Beispielsweise können Sie eigene Bereitstellungsschritte ausführen, wenn Sie beim Bereitstellen oder Zurückziehen ein Projekts oder Sie zusätzliche benutzerdefinierte Aufgaben ausführen können, bei der Ausführung von Visual Studio bestimmte Bereitstellungsschritte erstellen. Weitere Informationen finden Sie unter [Erweitern von SharePoint-Packen und-Bereitstellen](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
## <a name="common-development-tasks"></a>Allgemeine Aufgaben bei der Anwendungsentwicklung
 Sie können die folgenden allgemeinen Aufgaben in Erweiterungen des SharePoint-Projektsystem ausführen:  
  
-   Speichern Sie die benutzerdefinierte Zeichenfolgendaten mit Projektelemente und in verschiedene Typen von Projektdateien. Weitere Informationen finden Sie unter [speichern Daten in Erweiterungen des SharePoint-Projektsystem](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
-   Konvertieren eines Objekts in der SharePoint-Projektsystem in ein entsprechendes Objekt in der Visual Studio-Automatisierungsobjektmodell oder-Integrationsobjektmodell und umgekehrt. Weitere Informationen finden Sie unter [Konvertieren zwischen SharePoint-Projektsystemtypen und anderen Visual Studio-Projekttypen](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
## <a name="see-also"></a>Siehe auch
 [Definieren von benutzerdefinierten SharePoint-Projektelementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Erweitern von SharePoint-Projektelementen](../sharepoint/extending-sharepoint-project-items.md)   
 [Erweitern von SharePoint-Projekten](../sharepoint/extending-sharepoint-projects.md)   
 [Erweitern von SharePoint-Packen und-bereitstellen](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Speichern von Daten in Erweiterungen des SharePoint-Projektsystems](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Konvertieren zwischen SharePoint-Projektsystemtypen und anderen Visual Studio-Projekttypen](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Programmierkonzepte und Funktionen für Erweiterungen für SharePoint-Tools](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
  
  
