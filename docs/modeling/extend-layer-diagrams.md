---
title: Erweitern von Abhängigkeitsdiagrammen
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a8297ede4ce703c738133952bb13669ef6a6637
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645682"
---
# <a name="extend-dependency-diagrams"></a>Erweitern von Abhängigkeitsdiagrammen

Sie können Code schreiben, um Abhängigkeits Diagramme zu erstellen und zu aktualisieren und die Struktur Ihres Programmcodes mit Abhängigkeits Diagrammen in Visual Studio zu validieren. Sie können Befehle hinzufügen, die im Kontextmenü der Diagramme angezeigt werden, Drag & Drop-Gesten anpassen und über Textvorlagen auf das Ebenenmodell zugreifen. Sie können diese Erweiterung in einer Visual Studio Integration Extension (VSIX) verpacken und sie an andere Visual Studio-Benutzer verteilen.

## <a name="requirements"></a>Anforderungen

Auf dem Computer, auf dem Sie die Ebenenerweiterungen entwickeln möchten, muss Folgendes installiert sein:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- Modellierungs-SDK für Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Auf dem Computer, auf dem Sie die Ebenenerweiterungen ausführen möchten, muss eine passende Edition von Visual Studio installiert sein. Welche Editionen von Visual Studio Abhängigkeits Diagramme unterstützen, erfahren Sie unter [Editions Unterstützung für Architektur-und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="see-also"></a>Siehe auch

- [Abhängigkeitsdiagramme: Referenz](../modeling/layer-diagrams-reference.md)
- [Abhängigkeitsdiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)
- [Erstellen von Abhängigkeitsdiagrammen aus dem Code](../modeling/create-layer-diagrams-from-your-code.md)
- [Überprüfen von Code mit Abhängigkeitsdiagrammen](../modeling/validate-code-with-layer-diagrams.md)
