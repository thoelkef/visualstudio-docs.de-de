---
title: Elemente eines Projektmodells | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf847e35878dc84bb32fe81053c01c23e565fc4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708527"
---
# <a name="elements-of-a-project-model"></a>Elemente eines Projektmodells
Die Schnittstellen und Implementierungen aller [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekte in teilen sich eine grundlegende Struktur: das Projektmodell für Ihren Projekttyp. In Ihrem Projektmodell, dem VSPackage, das Sie entwickeln, erstellen Sie Objekte, die Ihren Entwurfsentscheidungen entsprechen, und arbeiten mit der globalen Funktionalität der IDE zusammen. Obwohl Sie steuern, wie ein Projektelement beibehalten wird, können Sie z. B. keine Benachrichtigung darüber steuern, dass eine Datei beibehalten werden muss. Wenn ein Benutzer den Fokus auf ein geöffnetes **File** Projektelement legt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und im Menü Datei in der Menüleiste **speichern** auswählt, muss der Projekttypcode den Befehl aus der IDE abfangen, die Datei beibehalten und eine Benachrichtigung an die IDE zurücksenden, dass die Datei nicht mehr geändert wird.

 Ihr VSPackage interagiert mit der IDE über Dienste, die Zugriff auf die IDE-Schnittstellen bieten. Beispielsweise überwachen und routen Sie über bestimmte Dienste Befehle und stellen Kontextinformationen für die im Projekt getroffenen Auswahlen bereit. Alle globalen IDE-Funktionen, die für Ihr VSPackage benötigt werden, werden von Diensten bereitgestellt. Weitere Informationen zu Diensten finden Sie unter [Gewusst wie: Abrufen eines Dienstes](../../extensibility/how-to-get-a-service.md).

 Weitere Überlegungen zur Umsetzung:

- Ein einzelnes Projektmodell kann mehr als einen Projekttyp enthalten.

- Projekttypen und die dazugehörigen Projektfabriken werden unabhängig von GUIDs registriert.

- Jedes Projekt muss über eine Vorlagendatei oder einen Assistenten verfügen, um die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] neue Projektdatei zu initialisieren, wenn ein Benutzer ein neues Projekt über die Benutzeroberfläche erstellt. Beispielsweise initialisieren [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] die Vorlagen, was schließlich zu .vcproj-Dateien wird.

  Die folgende Abbildung zeigt die primären Schnittstellen, Dienste und Objekte, aus denen eine typische Projektimplementierung besteht. Sie können den Anwendungshelfer `HierUtil7`verwenden, , um die zugrunde liegenden Objekte und andere Programmierbausteine zu erstellen. Weitere Informationen zum `HierUtil7` Anwendungshilfsprogramm finden Sie unter Verwenden von [HierUtil7-Projektklassen zum Implementieren eines Projekttyps (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

  ![Visual Studio-Projektmodellgrafik](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel") Projektmodell

  Weitere Informationen zu den im vorherigen Diagramm aufgeführten Schnittstellen und Diensten und anderen optionalen Schnittstellen, die nicht im Diagramm enthalten sind, finden Sie unter [Projektmodell-Kernkomponenten](../../extensibility/internals/project-model-core-components.md).

  Projekte können Befehle unterstützen und <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> müssen daher die Schnittstelle implementieren, um über die Befehlskontext-GUIDs am Befehlsrouting teilzunehmen.

## <a name="see-also"></a>Weitere Informationen
- [Checkliste: Neue Projekttypen erstellen](../../extensibility/internals/checklist-creating-new-project-types.md)
- [HierUtil7-Projektklassen verwenden, um einen Projekttyp (C++) zu implementieren](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Projektmodell-Kernkomponenten](../../extensibility/internals/project-model-core-components.md)
- [Erstellen von Projektinstanzen mithilfe von Projektfabriken](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [Gewusst wie: Holen Sie sich einen Service](../../extensibility/how-to-get-a-service.md)
- [Erstellen von Projekttypen](../../extensibility/internals/creating-project-types.md)
