---
title: Erweitern des SharePoint-Projektsystems | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7dce10c2bc44eb4fde6a6e38417d136ea5e9ba41
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061605"
---
# <a name="extend-the-sharepoint-project-system"></a>Erweitern von SharePoint-Projektsystem
  Sie können SharePoint-Lösungen erstellen, indem Sie mit der eine Reihe von Projektvorlagen und Elementvorlagen in Visual Studio. Diese Vorlagen erfüllen die Anforderungen der viele Entwicklungsszenarien, jedoch können Sie ermitteln, einige Fälle, in dem diese Funktionalität nicht bereitstellen, die erforderlich sind. In diesen Fällen können Sie die SharePoint-Projektsystem erweitern.

## <a name="overview-of-the-sharepoint-project-system"></a>Übersicht über die SharePoint-Projektsystem
 SharePoint-Projektsystem basiert darauf, dass die grundlegende Komponente *SharePoint-Projektelemente*. SharePoint-Projektelements darstellt, eine SharePoint-Anpassung, z. B. eine Listendefinition, Webparts und Inhaltstyp.

 Ein SharePoint-Projekt ist ein Visual Studio-Projekt, das eine oder mehrere SharePoint-Projektelemente enthält. SharePoint-Projekte enthalten auch zusätzliche Komponenten, die definieren, wie die Projektelemente in die Funktionen und Pakete für die Bereitstellung gruppiert werden.

 Weitere Informationen zum Inhalt der SharePoint-Projektelemente und SharePoint-Projekte, finden Sie unter [Erstellen von Vorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

## <a name="how-to-extend-the-sharepoint-project-system"></a>Erweitern der SharePoint-Projektsystem
 Sie können SharePoint-Projektsystem erweitern, es gibt folgende Möglichkeiten:

- Definieren Sie eigene SharePoint-Projektelementtypen, und ordnen sie neue Vorlagen oder Projektvorlagen in Visual Studio. Beispielsweise können Sie einen SharePoint-Projektelementtyp definieren, für das Erstellen einer benutzerdefinierten Aktion oder ein Feld. Weitere Informationen finden Sie unter [definieren Sie benutzerdefinierte SharePoint-Projektelementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md).

- Erweitern Sie SharePoint-Projektelementtypen, die in Visual Studio bereits installiert sind. Sie können z. B. ein Kontextmenüelement hinzufügen, auf ein Projektelement in **Projektmappen-Explorer** und passen Sie das Projektelement aus, wenn ein Entwickler das Menüelement auswählt. Weitere Informationen finden Sie unter [Erweitern von SharePoint-Projektelemente](../sharepoint/extending-sharepoint-project-items.md).

- Erweitern Sie SharePoint-Projekte. Beispielsweise können Sie Ereignishandler, um bestimmte Aufgaben auszuführen, wenn Elemente hinzugefügt oder aus SharePoint-Projekten entfernt hinzufügen. Weitere Informationen finden Sie unter [Erweitern von SharePoint-Projekte](../sharepoint/extending-sharepoint-projects.md).

- Erweitern Sie das Verhalten Verpacken und Bereitstellen von SharePoint-Projektelemente und SharePoint-Projekte. Beispielsweise können Sie durch Erstellen eigener Bereitstellungsschritte ausgeführt werden, wenn Sie beim Bereitstellen oder Zurückziehen ein Projekts oder Sie zusätzliche benutzerdefinierte Aufgaben ausführen können, wenn Visual Studio bestimmte Bereitstellungsschritte ausgeführt wird. Weitere Informationen finden Sie unter [Erweitern von SharePoint-Packen und-Bereitstellen](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

## <a name="common-development-tasks"></a>Allgemeine Entwicklungsaufgaben
 In Erweiterungen des SharePoint-Projektsystem können Sie die folgenden allgemeinen Aufgaben ausführen:

- Speichern Sie die benutzerdefinierten Zeichenfolgendaten mit Projektelementen und in verschiedene Arten von Projektdateien. Weitere Informationen finden Sie unter [Speichern von Daten in Erweiterungen des SharePoint-Projektsystem](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

- Konvertieren eines Objekts in der SharePoint-Projektsystem in ein entsprechendes Objekt in der Visual Studio-Automatisierungsobjektmodell oder-Integrationsobjektmodell und umgekehrt. Weitere Informationen finden Sie unter [konver zwischen SharePoint-Projektsystemtypen und anderen Visual Studio-Projekttypen](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

## <a name="see-also"></a>Siehe auch
- [Definieren von benutzerdefinierten SharePoint-Projektelementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Erweitern von SharePoint-Projektelemente](../sharepoint/extending-sharepoint-project-items.md)
- [Erweitern von SharePoint-Projekte](../sharepoint/extending-sharepoint-projects.md)
- [Erweitern von SharePoint-Packen und-bereitstellen](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Speichern von Daten in Erweiterungen des SharePoint-Projektsystem](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Konvertieren Sie zwischen SharePoint-Projektsystemtypen und anderen Visual Studio-Projekttypen](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Erweitern von SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Programmierkonzepte und Funktionen für Erweiterungen für SharePoint-Tools](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
