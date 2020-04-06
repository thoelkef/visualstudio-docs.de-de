---
title: Projekttyp Essentials | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b44da532207668d9526aec0ccdcab027b94184e6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706384"
---
# <a name="project-type-essentials"></a>Grundlagen zu Projekttypen
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]enthält mehrere Projekttypen für [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]Sprachen wie oder . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Können Sie auch eigene Projekttypen erstellen.

 Wenn Sie nur benutzerdefinierte Befehle, Editoren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]oder Toolfenster hinzufügen möchten, können Sie dies tun, ohne einen neuen Projekttyp zu erstellen. Weitere Informationen finden Sie in den folgenden Themen:

- [Befehle, Menüs und Symbolleisten](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Editor- und Sprachdiensterweiterungen](../../extensibility/editor-and-language-service-extensions.md)

- [Erweitern und Anpassen von Toolfenstern](../../extensibility/extending-and-customizing-tool-windows.md)

  Wenn Sie das Verhalten der bereitgestellten [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Und Projekttypen anpassen möchten, können Sie dies auch mithilfe von Projektuntertypen tun. Weitere Informationen finden Sie unter [Projektuntertypen](../../extensibility/internals/project-subtypes.md).

  Sie müssen einen neuen Projekttyp für Projekte erstellen, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] die auf einer anderen Sprache als einer anderen Sprache basieren und eine oder mehrere der folgenden Optionen unterstützen möchten:

- Build

- Bereitstellung

- Mehrere Konfigurationen

- Quellcodeverwaltung

- Debuggen

- Projektelemente im Projektmappen-Explorer

- Die Dialogfelder **"Projekt öffnen"** oder **"Neues Projekt"**

- Projektverschachtelung

- Weitere Informationen zu den Funktionen von Projekttypen finden Sie im Folgenden:

- Projekttypen sind Objekte in einem VSPackage, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die den erwarteten Satz von Schnittstellen implementieren. Wenn Sie zum Entwickeln eines Projekttyps mit dem Projekttyp "C" beginnen, implementieren die Projektklassen Managed Package Framework die für Sie erforderlichen Schnittstellen und lassen Sie diese Implementierung erben. Weitere Informationen finden Sie unter [Verwenden des Managed Package Framework zum Implementieren eines Projekttyps ( C' ).](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md)

- Für C++-Entwickler funktionieren die Klassen in der HierUtil-Bibliothek auf ähnliche Weise. Weitere Informationen finden Sie unter [Nicht in Build: Verwenden von HierUtil7-Projektklassen zum Implementieren eines Projekttyps (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

- Projekttypen können andere Daten als typische Quellcodedateien unterstützen, die in eine EXE- oder DLL-Assembly integriert werden. Datenbankprojekte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] enthalten beispielsweise Verweise auf Skript- und Abfragedateien, die auf dem Datenträger gespeichert sind, und fügen Dem **Projektmappen-Explorer** Befehle zum Ausführen der Skripts und Abfragen für eine Datenbank hinzu, die Projekte unterstützen jedoch kein Buildverhalten. Weitere Informationen finden Sie unter [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md).

- Ein Projekttyp muss überhaupt keine Dateien verwenden. Beispielsweise kann ein Projekttyp alle seine Daten in einer Datenbank speichern. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]gibt Projekttypen vollständige Kontrolle darüber, wie sie Daten für Projekte und Projektelemente beibehalten. Weitere Informationen finden Sie unter [Projekttypentwurfsentscheidungen](../../extensibility/internals/project-type-design-decisions.md).

- Projekttypen müssen eine *Projektfactory*bereitstellen, bei der es sich [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] um ein Objekt handelt, das eine Instanz des Projekttyps erstellt, wenn ein Projekt geöffnet oder erstellt wird, das auf diesem Projekttyp basiert. Weitere Informationen finden Sie unter [Erstellen von Projektinstanzen mithilfe von Projektfabriken](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

- Projekttypen müssen Vorlagen für Projekte und Projektelemente bereitstellen. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]verwendet die Vorlagen, wenn Benutzer neue Projekte erstellen und vorhandenen Projekten neue Elemente hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md).

- Projekttypen können mehrere Konfigurationen unterstützen, z. B. Debug und Release. Benutzer können die verschiedenen Konfigurationen eines Projekts mithilfe von von Ihnen gelieferten Eigenschaftenseiten ändern. Weitere Informationen finden Sie unter [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md).

## <a name="see-also"></a>Weitere Informationen
- [Bereitstellen von Projekttypen](../../extensibility/internals/deploying-project-types.md)
