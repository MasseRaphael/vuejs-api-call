<template>
    <div>
        <header>
            <h1>{{ $static.metadata.siteName }}</h1>
        </header>
        <slot />
    </div>
</template>
<static-query>
query {
    metadata {
        siteName
    }
}
</static-query>