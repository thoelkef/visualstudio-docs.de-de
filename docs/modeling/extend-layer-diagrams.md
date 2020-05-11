---
title: Erweitern von Abhängigkeitsdiagrammen
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 305c562c7600dc6955ce0307db92f4e257fc1c21
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301488"
---
# <a name="extend-dependency-diagrams"></a>Erweitern von Abhängigkeitsdiagrammen

Sie können Code schreiben, um Abhängigkeitsdiagramme zu erstellen und zu aktualisieren und die Struktur des Programmcodes anhand von Abhängigkeitsdiagrammen in Visual Studio zu überprüfen. Sie können Befehle hinzufügen, die im Kontextmenü der Diagramme angezeigt werden, Drag & Drop-Gesten anpassen und über Textvorlagen auf das Ebenenmodell zugreifen. Sie können diese Erweiterung in einer Visual Studio Integration Extension (VSIX) verpacken und sie an andere Visual Studio-Benutzer verteilen.

## <a name="requirements"></a>Requirements (Anforderungen)

Auf dem Computer, auf dem Sie die Ebenenerweiterungen entwickeln möchten, muss Folgendes installiert sein:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- Modellieren von SDK für Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Sie müssen eine geeignete Edition von Visual Studio auf dem Computer installiert haben, auf dem Sie die Layer-Erweiterungen ausführen möchten. Informationen dazu, welche Editionen von Visual Studio Abhängigkeitsdiagramme unterstützen, finden Sie unter [Editionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="see-also"></a>Weitere Informationen

- [Abhängigkeitsdiagramme: Referenz](../modeling/layer-diagrams-reference.md)
- [Abhängigkeitsdiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)
- [Erstellen von Abhängigkeitsdiagrammen aus dem Code](../modeling/create-layer-diagrams-from-your-code.md)
- [Überprüfen von Code mit Abhängigkeitsdiagrammen](../modeling/validate-code-with-layer-diagrams.md)
