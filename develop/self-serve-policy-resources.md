---
title: Recursos de política de autosserviço
description: Um parceiro define políticas de autosserviço para um cliente.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e44581b805e076132984b67280699314e274ca94
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446722"
---
# <a name="selfservepolicy-resource"></a><span data-ttu-id="32a39-103">Recurso SelfServePolicy</span><span class="sxs-lookup"><span data-stu-id="32a39-103">SelfServePolicy resource</span></span>

<span data-ttu-id="32a39-104">Um parceiro define políticas de autosserviço para um cliente.</span><span class="sxs-lookup"><span data-stu-id="32a39-104">A partner sets self serve policies for a customer.</span></span>

## <a name="selfservepolicy"></a><span data-ttu-id="32a39-105">AutoServePolicy</span><span class="sxs-lookup"><span data-stu-id="32a39-105">SelfServePolicy</span></span>

<span data-ttu-id="32a39-106">Descreve um carrinho.</span><span class="sxs-lookup"><span data-stu-id="32a39-106">Describes a cart.</span></span>

| <span data-ttu-id="32a39-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="32a39-107">Property</span></span>              | <span data-ttu-id="32a39-108">Tipo</span><span class="sxs-lookup"><span data-stu-id="32a39-108">Type</span></span>             | <span data-ttu-id="32a39-109">Description</span><span class="sxs-lookup"><span data-stu-id="32a39-109">Description</span></span>                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="32a39-110">ID</span><span class="sxs-lookup"><span data-stu-id="32a39-110">id</span></span>                    | <span data-ttu-id="32a39-111">string</span><span class="sxs-lookup"><span data-stu-id="32a39-111">string</span></span>           | <span data-ttu-id="32a39-112">Um identificador de política de autosserviço que é fornecido após a criação bem sucedida da política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="32a39-112">A self-serve policy identifier that is supplied upon successful creation of the self serve policy.</span></span>     |
| <span data-ttu-id="32a39-113">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="32a39-113">SelfServeEntity</span></span>       | <span data-ttu-id="32a39-114">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="32a39-114">SelfServeEntity</span></span>  | <span data-ttu-id="32a39-115">A entidade self-serve a quem está a ser concedido acesso.</span><span class="sxs-lookup"><span data-stu-id="32a39-115">The self serve entity that is being granted access.</span></span>                                                     |
| <span data-ttu-id="32a39-116">Grantor</span><span class="sxs-lookup"><span data-stu-id="32a39-116">Grantor</span></span>               | <span data-ttu-id="32a39-117">Grantor</span><span class="sxs-lookup"><span data-stu-id="32a39-117">Grantor</span></span>          | <span data-ttu-id="32a39-118">O concededor que está a conceder acesso.</span><span class="sxs-lookup"><span data-stu-id="32a39-118">The grantor that is granting access.</span></span>                                                                    |
| <span data-ttu-id="32a39-119">Permissões</span><span class="sxs-lookup"><span data-stu-id="32a39-119">Permissions</span></span>           | <span data-ttu-id="32a39-120">Matriz de Permissão</span><span class="sxs-lookup"><span data-stu-id="32a39-120">Array of Permission</span></span>| <span data-ttu-id="32a39-121">Um conjunto de recursos [de permissão.](#permission)</span><span class="sxs-lookup"><span data-stu-id="32a39-121">An Array of [Permission](#permission) resources.</span></span>                                                                     |

## <a name="selfserveentity"></a><span data-ttu-id="32a39-122">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="32a39-122">SelfServeEntity</span></span>

<span data-ttu-id="32a39-123">Representa a entidade que recebe permissões.</span><span class="sxs-lookup"><span data-stu-id="32a39-123">Represents the entity being granted permissions.</span></span>

| <span data-ttu-id="32a39-124">Propriedade</span><span class="sxs-lookup"><span data-stu-id="32a39-124">Property</span></span>             | <span data-ttu-id="32a39-125">Tipo</span><span class="sxs-lookup"><span data-stu-id="32a39-125">Type</span></span>|<span data-ttu-id="32a39-126">Description</span><span class="sxs-lookup"><span data-stu-id="32a39-126">Description</span></span>|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| <span data-ttu-id="32a39-127">SelfServeEntityType</span><span class="sxs-lookup"><span data-stu-id="32a39-127">SelfServeEntityType</span></span>  | <span data-ttu-id="32a39-128">string</span><span class="sxs-lookup"><span data-stu-id="32a39-128">string</span></span>                           | <span data-ttu-id="32a39-129">A entidade a quem foi concedido acesso, valores aceites: Cliente.</span><span class="sxs-lookup"><span data-stu-id="32a39-129">The entity being granted access, accepted values: Customer.</span></span>                                 |
| <span data-ttu-id="32a39-130">TenantID</span><span class="sxs-lookup"><span data-stu-id="32a39-130">TenantID</span></span>             | <span data-ttu-id="32a39-131">string</span><span class="sxs-lookup"><span data-stu-id="32a39-131">string</span></span>                           | <span data-ttu-id="32a39-132">O identificador de inquilino da entidade que tem acesso.</span><span class="sxs-lookup"><span data-stu-id="32a39-132">The tenant identifier of the entity being granted access.</span></span>                                   |

## <a name="grantor"></a><span data-ttu-id="32a39-133">Grantor</span><span class="sxs-lookup"><span data-stu-id="32a39-133">Grantor</span></span>

<span data-ttu-id="32a39-134">Representa o concededor que concede as permissões.</span><span class="sxs-lookup"><span data-stu-id="32a39-134">Represents the grantor granting the permissions.</span></span>

| <span data-ttu-id="32a39-135">Propriedade</span><span class="sxs-lookup"><span data-stu-id="32a39-135">Property</span></span>             | <span data-ttu-id="32a39-136">Tipo</span><span class="sxs-lookup"><span data-stu-id="32a39-136">Type</span></span>|<span data-ttu-id="32a39-137">Description</span><span class="sxs-lookup"><span data-stu-id="32a39-137">Description</span></span>|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| <span data-ttu-id="32a39-138">GrantorType</span><span class="sxs-lookup"><span data-stu-id="32a39-138">GrantorType</span></span>          | <span data-ttu-id="32a39-139">string</span><span class="sxs-lookup"><span data-stu-id="32a39-139">string</span></span>                           | <span data-ttu-id="32a39-140">O bolseiro que concede acesso, valores aceites: BillToPartner.</span><span class="sxs-lookup"><span data-stu-id="32a39-140">The grantor granting access, accepted values: BillToPartner.</span></span>                               |
| <span data-ttu-id="32a39-141">TenantID</span><span class="sxs-lookup"><span data-stu-id="32a39-141">TenantID</span></span>             | <span data-ttu-id="32a39-142">string</span><span class="sxs-lookup"><span data-stu-id="32a39-142">string</span></span>                           | <span data-ttu-id="32a39-143">O identificador de inquilino da entidade que concede acesso.</span><span class="sxs-lookup"><span data-stu-id="32a39-143">The tenant identifier of the entity granting access.</span></span>                                       |


## <a name="permission"></a><span data-ttu-id="32a39-144">Permissão</span><span class="sxs-lookup"><span data-stu-id="32a39-144">Permission</span></span>

<span data-ttu-id="32a39-145">Representa uma permissão na política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="32a39-145">Represents a permission in the self serve policy.</span></span>

| <span data-ttu-id="32a39-146">Propriedade</span><span class="sxs-lookup"><span data-stu-id="32a39-146">Property</span></span>             | <span data-ttu-id="32a39-147">Tipo</span><span class="sxs-lookup"><span data-stu-id="32a39-147">Type</span></span>|<span data-ttu-id="32a39-148">Description</span><span class="sxs-lookup"><span data-stu-id="32a39-148">Description</span></span>|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| <span data-ttu-id="32a39-149">Recurso</span><span class="sxs-lookup"><span data-stu-id="32a39-149">Resource</span></span>             | <span data-ttu-id="32a39-150">string</span><span class="sxs-lookup"><span data-stu-id="32a39-150">string</span></span>                           | <span data-ttu-id="32a39-151">O acesso ao recurso também está a ser concedido: AzureReservedInstances.</span><span class="sxs-lookup"><span data-stu-id="32a39-151">The resource access is being granted too: AzureReservedInstances.</span></span>                          |
| <span data-ttu-id="32a39-152">Ação</span><span class="sxs-lookup"><span data-stu-id="32a39-152">Action</span></span>               | <span data-ttu-id="32a39-153">string</span><span class="sxs-lookup"><span data-stu-id="32a39-153">string</span></span>                           | <span data-ttu-id="32a39-154">O acesso à ação está a ser concedido para: Compra</span><span class="sxs-lookup"><span data-stu-id="32a39-154">The action access is being granted for: Purchase</span></span>                                           |
