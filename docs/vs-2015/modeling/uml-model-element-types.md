---
title: Типы элементов модели UML | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, types
ms.assetid: 25345a53-7246-4eb7-8ad9-0b695aa171a2
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 54036b985c90be926eaa56f6ebe60d1f3903e0b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657312"
---
# <a name="uml-model-element-types"></a>Типы элементов модели UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете считывать модель UML и выполнять с ней действия посредством программного интерфейса. В этом разделе приведены краткие сведения об иерархии типов элементов. Эта иерархия совпадает с иерархией, определенной в спецификации UML.

 Сведения о каждом типе приведены в [справочнике по API для расширяемости моделирования UML](../modeling/api-reference-for-uml-modeling-extensibility.md).

## <a name="element-types"></a>Типы элементов
 Это набор типов, определенных в сборке `Microsoft.VisualStudio.Uml.Interfaces.dll`.

 Полное имя каждого элемента — это `Microsoft.VisualStudio.Uml.`, за которым следует имя из списка.

 Для удобства этот список построен как иерархия наследования. Если тип имеет несколько супертипов, дополнительные супертипы перечисляются после двоеточия (:).

```

Classes.IElement
|  Activities.IActivityGroup
|  Classes.IComment
|  Classes.IMultiplicityElement
|  |  CompositeStructures.IConnectorEnd
|  Classes.INamedElement
|  |  Deployments.IDeployedArtifact
|  |  Deployments.IDeploymentTarget
|  |  |  Classes.IInstanceSpecification
             : Deployments.IDeployedArtifact,
               Deployments.IDeploymentTarget
|  |  |  |  Classes.IEnumerationLiteral
|  |  Interactions.IInteractionFragment
|  |  |  Interactions.ICombinedFragment
|  |  |  |  Interactions.IConsiderIgnoreFragment
|  |  |  Interactions.IExecutionSpecification
|  |  |  |  Interactions.IActionExecutionSpecification
|  |  |  |  Interactions.IBehaviorExecutionSpecification
|  |  |  Interactions.IInteraction  : CommonBehaviors.IBehavior
|  |  |  Interactions.IInteractionOperand : Classes.INamespace
|  |  |  Interactions.IInteractionUse
|  |  |  Interactions.IOccurrenceSpecification
|  |  |  |  Interactions.IExecutionOccurrenceSpecification
|  |  |  |  Interactions.IMessageOccurrenceSpecification
                   : Interactions.IMessageEnd
|  |  |  |  |  Interactions.ILostFoundTarget
|  |  |  |  Interactions.IOperandOccurrenceSpecification
|  |  |  Interactions.IStateInvariant
|  |  Interactions.ILifeline
|  |  Interactions.IMessage
|  |  Interactions.IMessageEnd
|  |  Classes.INamespace
|  |  |  Classes.IPackage
             : Classes.IPackageableElement,
              AuxiliaryConstructs.ITemplateableElement
|  |  |  |  AuxiliaryConstructs.IModel
|  |  |  Activities.IState
|  |  Classes.IPackageableElement
                   : AuxiliaryConstructs.IParameterableElement
|  |  |  Classes.IConstraint
|  |  |  |  Interactions.IInteractionConstraint
|  |  |  CommonBehaviors.IEvent
|  |  |  |  Interactions.IExecutionEvent
|  |  |  |  CommonBehaviors.IMessageEvent
|  |  |  |  |  CommonBehaviors.ICallEvent
|  |  |  |  |  Interactions.IReceiveOperationEvent
|  |  |  |  |  Interactions.IReceiveSignalEvent
|  |  |  |  |  Interactions.ISendOperationEvent
|  |  |  |  |  Interactions.ISendSignalEvent
|  |  |  Classes.IType
|  |  |  |  Classes.IClassifier : Classes.INamespace, Classes.IRedefinableElement, AuxiliaryConstructs.ITemplateableElement
|  |  |  |  |  Deployments.IArtifact
                   : Deployments.IDeployedArtifact
|  |  |  |  |  |  Deployments.IDeploymentSpecification
|  |  |  |  |  CommonBehaviors.IBehavioredClassifier
|  |  |  |  |  |  UseCases.IActor
|  |  |  |  |  |  Classes.IClass
                         : CompositeStructures.IEncapsulatedClassifier
|  |  |  |  |  |  |  CommonBehaviors.IBehavior
|  |  |  |  |  |  |  |  Activities.IActivity
|  |  |  |  |  |  |  Components.IComponent
|  |  |  |  |  |  |  |  UseCases.ISubsystem
|  |  |  |  |  |  |  Deployments.INode : IDeploymentTarget
|  |  |  |  |  |  |  |  Deployments.IDevice
|  |  |  |  |  |  |  |  Deployments.IExecutionEnvironment
|  |  |  |  |  |  UseCases.IUseCase
|  |  |  |  |  Classes.IDataType
|  |  |  |  |  |  Classes.IEnumeration
|  |  |  |  |  |  Classes.IPrimitiveType
|  |  |  |  |  Classes.IInterface
|  |  |  |  |  CompositeStructures.IStructuredClassifier
|  |  |  |  |  |  CompositeStructures.IEncapsulatedClassifier
|  |  |  Classes.IValueSpecification : Classes.ITypedElement
|  |  |  |  Classes.IExpression
|  |  |  |  Classes.IInstanceValue
|  |  |  |  Classes.ILiteralSpecification
|  |  |  |  |  Classes.ILiteralBoolean
|  |  |  |  |  Classes.ILiteralInteger
|  |  |  |  |  Classes.ILiteralNull
|  |  |  |  |  Classes.ILiteralString
|  |  |  |  |  Classes.ILiteralUnlimitedNatural
|  |  |  |  Classes.IOpaqueExpression
|  |  Classes.IRedefinableElement
|  |  |  Activities.IActivityNode
|  |  |  |  Activities.IControlNode
|  |  |  |  |  Activities.IDecisionNode
|  |  |  |  |  Activities.IFinalNode
|  |  |  |  |  |  Activities.IActivityFinalNode
|  |  |  |  |  Activities.IForkNode
|  |  |  |  |  Activities.IInitialNode
|  |  |  |  |  Activities.IJoinNode
|  |  |  |  |  Activities.IMergeNode
|  |  |  |  Activities.IExecutableNode
|  |  |  |  |  Actions.IAction
|  |  |  |  |  |  Actions.IAcceptEventAction
|  |  |  |  |  |  Actions.ICreateObjectAction
|  |  |  |  |  |  Actions.IInvocationAction
|  |  |  |  |  |  |  Actions.ICallAction
|  |  |  |  |  |  |  |  Actions.ICallBehaviorAction
|  |  |  |  |  |  |  |  Actions.ICallOperationAction
|  |  |  |  |  |  |  Actions.ISendSignalAction
|  |  |  |  |  |  Actions.IOpaqueAction
|  |  |  |  Activities.IObjectNode  : Classes.ITypedElement
|  |  |  |  |  Activities.IActivityParameterNode
|  |  |  |  |  Actions.IPin : Classes.IMultiplicityElement
|  |  |  |  |  |  Actions.IInputPin
|  |  |  |  |  |  Actions.IOutputPin
|  |  |  UseCases.IExtensionPoint
|  |  |  Classes.IFeature
|  |  |  |  Classes.IBehavioralFeature  : Classes.INamespace
|  |  |  |  |  Classes.IOperation
                   : AuxiliaryConstructs.ITemplateableElement,
                   AuxiliaryConstructs.IParameterableElement
|  |  |  |  Classes.IStructuralFeature
              : Classes.IMultiplicityElement,
                Classes.ITypedElement
|  |  |  |  |  Classes.IProperty
                   : AuxiliaryConstructs.ITemplateableElement,
                   CompositeStructures.IConnectableElement,
                   Deployments.IDeploymentTarget
|  |  |  |  |  |  CompositeStructures.IPort
|  |  Classes.ITypedElement
|  |  |  CompositeStructures.IConnectableElement
             : AuxiliaryConstructs.IParameterableElement
|  |  |  Classes.IParameter  : Classes.IMultiplicityElement, CompositeStructures.IConnectableElement
|  AuxiliaryConstructs.IParameterableElement
|  Classes.IProfileInstance

|  Classes.IRelationship
|  |  Activities.IActivityEdge : Classes.IRedefinableElement
|  |  |  Activities.IControlFlow
|  |  |  Activities.IObjectFlow
|  |  Classes.IAssociation : IClassifier
|  |  |  Deployments.ICommunicationPath
|  |  CompositeStructures.IConnector
|  |  Classes.IDirectedRelationship
|  |  |  Classes.IDependency : Classes.IPackageableElement
|  |  |  |  Classes.IAbstraction
|  |  |  |  |  Deployments.IManifestation
|  |  |  |  |  Classes.IRealization
|  |  |  |  |  |  Classes.IInterfaceRealization
|  |  |  |  Deployments.IDeployment
|  |  |  |  Classes.IUsage
|  |  |  UseCases.IExtend : Classes.INamedElement
|  |  |  Classes.IGeneralization
|  |  |  UseCases.IInclude : Classes.INamedElement
|  |  |  Classes.IPackageImport
|  |  |  AuxiliaryConstructs.ITemplateBinding
|  Classes.IStereotypeInstance
|  Classes.IStereotypePropertyInstance
|  AuxiliaryConstructs.ITemplateableElement
|  AuxiliaryConstructs.ITemplateParameter
|  |  AuxiliaryConstructs.IClassifierTemplateParameter
|  |  AuxiliaryConstructs.IOperationTemplateParameter
|  AuxiliaryConstructs.ITemplateParameterSubstitution
|  AuxiliaryConstructs.ITemplateSignature
|  |  AuxiliaryConstructs.IRedefinableTemplateSignature
             : Classes.IRedefinableElement
```

## <a name="see-also"></a>См. также:
 [Определение профиля для расширения](../modeling/define-a-profile-to-extend-uml.md) [ограничений проверки UML для](../modeling/define-validation-constraints-for-uml-models.md) [справочника по API моделей UML для расширяемости моделирования UML](../modeling/api-reference-for-uml-modeling-extensibility.md)
