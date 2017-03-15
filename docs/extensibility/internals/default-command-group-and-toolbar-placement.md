---
title: "Standardbefehl, Gruppen- und Platzierung der Symbolleiste | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Standardgruppen-Befehle [Visual Studio]"
  - "Standard-Symbolleisten [Visual Studio]"
  - "Standard-Editor-Befehle [Visual Studio]"
  - "Befehlsgruppen"
  - "Standard-IDE-Befehle [Visual Studio]"
  - "Standard-Product-Befehle [Visual Studio]"
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
caps.latest.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 30
---
# Standardbefehl, Gruppen- und Platzierung der Symbolleiste
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Für Produkt Einheitlichkeit und Stabilität der Benutzeroberfläche bestimmte Befehlsgruppen wird standardmäßig angezeigt und [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] enthält Definitionen für Befehle und Befehlsgruppen. VSPackages können sich auch auf die Standardbefehle und Befehlsgruppen aus.  
  
 Der Befehl Standardgruppen fallen in drei Kategorien: IDE Befehle, Produkt und Editor\-Befehle.  
  
## Standard\-IDE\-Befehle  
 Die Standard\-IDE\-Symbolleiste enthält Befehle, die von allen Produkten enthalten, die freigegebenen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Hierzu gehören auch Befehle, die im Zusammenhang mit generischen Projektvorgänge, wie z. B. die **Speichern** Befehl und die **Hinzufügen** Befehl. VSPackages sollte nicht hinzufügen oder davon subtrahiert diese Symbolleiste, mit einer Ausnahme: Wenn das Produkt oder die VSPackage ein neues Toolfenster fügt, das Fenster sollte die Liste der verfügbaren Tools hinzugefügt werden, auf die **Ansicht** Menü. Neue Produkte oder VSPackages können eigene Symbolleiste hinzufügen.  
  
## Standardbefehle\-Produkt  
 Jedes Produkt kann die IDE mit eigenen Standardsymbolleiste bereitstellen, die enthält wichtige und häufig verwendete Befehle. Es ist jedoch am besten, vorhandenen Menüs und Symbolleisten möglichst und ergänzen sie mit anderen aufgabenspezifischen Symbolleisten nach Bedarf.  
  
 Das Prioritätsfeld für eine Symbolleiste bestimmt die Platzierung der Zeile. 0 \(null\) Priorität platziert die Symbolleiste auf die dritte Zeile \(Zeile 3\) unterhalb der Menüleiste \(Zeile 1\) und die **Standard** Symbolleiste \(Zeile 2\). Daher anderen Symbolleisten in Zeile angezeigt \(Priorität \+ 3\). Nachfolgende Symbolleisten werden auf der gleichen Zeile platziert, wenn genügend Platz vorhanden ist; Andernfalls werden sie automatisch auf die nächste Zeile verschoben.  
  
## Standard\-Editor\-Befehle  
 Ein VSPackage, das einen benutzerdefinierten Editor bietet sollte eine Standardsymbolleiste bereitstellen, die enthält die wichtigsten und häufig verwendete Befehle in diesem Editor. Die Editor\-Symbolleiste sollte angezeigt werden, wenn der Editor aktiv ist und ausgeblendet werden soll, wenn der Editor nicht aktiv ist. Die Sichtbarkeit wird gesteuert, der `VisibilityConstraints Element` der .vsct\-Datei.  
  
 Symbolleisten\-Editor\-sollte unter IDE und Produkt Symbolleisten platziert werden.  
  
## Siehe auch  
 [IDE\-definierte Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)