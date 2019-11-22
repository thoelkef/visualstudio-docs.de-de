---
title: 'How to: Respond to Changes in a UML Model | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: f0300371-9cac-4def-a3f5-7d7b62dcd6f3
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9eaaa1406591bc950dbbf95aff8dcd732eef3448
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74293403"
---
# <a name="how-to-respond-to-changes-in-a-uml-model"></a>Gewusst wie: Reagieren auf Änderungen in einem UML-Modell
Es ist möglich, Code zu schreiben, der ausgeführt wird, wenn eine Änderung an einem UML-Modell in Visual Studio stattfindet. Der Code reagiert gleichermaßen auf Änderungen, die direkt vom Benutzer und von anderen Visual Studio-Erweiterungen vorgenommen werden. Welche Versionen von Visual Studio UML-Modelle unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!WARNING]
> Diese Techniken werden von der UML-API nicht unterstützt. Sie funktionieren in zukünftigen Versionen von Visual Studio möglicherweise nicht.

## <a name="see-also"></a>Siehe auch
 [Navigate the UML model](../modeling/navigate-the-uml-model.md) [Event Handlers Propagate Changes Outside the Model](../modeling/event-handlers-propagate-changes-outside-the-model.md) [Sample: Color by Stereotype](https://go.microsoft.com/fwlink/?LinkId=213841)