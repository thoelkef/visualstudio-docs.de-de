---
title: Erweitern von ebenendiagrammen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, creating extensions
- layer models
ms.assetid: 83fca301-b008-485a-87eb-218050e71451
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bfcec64f9401fdbf79e67bee5fe8430452632fbc
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301027"
---
# <a name="extend-layer-diagrams"></a>Extend layer diagrams
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Code schreiben, um Ebenendiagramme zu erstellen und zu aktualisieren, und um die Struktur Ihres Programmcodes mit Ebenendiagrammen in Visual Studio abzugleichen. Sie können Befehle hinzufügen, die im Kontextmenü der Diagramme angezeigt werden, Drag & Drop-Gesten anpassen und über Textvorlagen auf das Ebenenmodell zugreifen. Sie können diese Erweiterung in einer Visual Studio Integration Extension (VSIX) verpacken und sie an andere Visual Studio-Benutzer verteilen.

 Weitere Informationen zu Ebenendiagrammen finden Sie unter:

- [Ebenendiagramme: Referenz](../modeling/layer-diagrams-reference.md)

- [Ebenendiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)

- [Erstellen von Ebenendiagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md)

- [Überprüfen von Code mit Ebenendiagrammen](../modeling/validate-code-with-layer-diagrams.md)

## <a name="prereqs"></a> Anforderungen
 Auf dem Computer, auf dem Sie die Ebenenerweiterungen entwickeln möchten, muss Folgendes installiert sein:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- [Modellierungs-SDK für Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48148)

  Sie müssen die passende Visual Studio-Version auf dem Computer installiert haben, auf dem Sie die Ebenenerweiterungen ausführen möchten. Weitere Informationen finden Sie unter Bereitstellen [einer ebenenmodellerweiterung](../modeling/deploy-a-layer-model-extension.md).

  Welche Versionen von Visual Studio Ebenendiagramme unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-section"></a>In diesem Abschnitt
 [Hinzufügen von Befehlen und Bewegungen zu Ebenendiagrammen](../modeling/add-commands-and-gestures-to-layer-diagrams.md)

 [Hinzufügen einer benutzerdefinierten Architekturvalidierung zu Ebenendiagrammen](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

 [Hinzufügen benutzerdefinierter Eigenschaften zu Ebenendiagrammen](../modeling/add-custom-properties-to-layer-diagrams.md)

 [Navigieren in und Aktualisieren von Ebenenmodellen im Programmcode](../modeling/navigate-and-update-layer-models-in-program-code.md)

 [Bereitstellen einer Ebenenmodellerweiterung](../modeling/deploy-a-layer-model-extension.md)

 [Problembehandlung bei Erweiterungen für Ebenendiagramme](../modeling/troubleshoot-extensions-for-layer-diagrams.md)

## <a name="see-also"></a>Siehe auch
 [Definieren und Installieren einer Modellierungs Erweiterung](../modeling/define-and-install-a-modeling-extension.md) [ebenendiagramme: Referenz](../modeling/layer-diagrams-reference.md) [ebenendiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md) [Erstellen von ebenendiagrammen aus dem Code](../modeling/create-layer-diagrams-from-your-code.md) [Überprüfen von Code mit ebenendiagrammen](../modeling/validate-code-with-layer-diagrams.md) [Generieren von Dateien aus einem UML-Modell](../modeling/generate-files-from-a-uml-model.md) [Öffnen eines UML-Modells mithilfe der Visual Studio-API](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)
