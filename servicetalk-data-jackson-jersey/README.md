# ServiceTalk Data Jackson Jersey

This module provides Jackson-based JSON serialization and deserialization for ServiceTalk Jersey router.
It is a replacement for `jersey-media-json-jackson` and allows avoiding the input stream adaptation that kicks in
with out-of-the-box body readers and also allows accepting/returning `Single<Pojo>` and `Publisher<Pojo>`
from resource methods.

## Using a custom ObjectMapper

If you have configured a Jackson `ObjectMapper` and want to use it with this module, you need to provide it to the
JAX-RS runtime as
a [`ContextResolver`](https://jax-rs.github.io/apidocs/2.1/index.html?javax/ws/rs/ext/ContextResolver.html).
To help with this, `ServiceTalkJacksonSerializerFeature` provides a helper method named `contextResolverFor` that
can build a `ContextResolver<JacksonSerializationProvider>` from an `ObjectMapper` instance.

It is up to the user to properly register this `ContextResolver` with their application.

## Using a custom JacksonSerializationProvider

Like with `ObjectMapper`, if you want to use a custom `ServiceTalkJacksonSerializerFeature` you need to provide it as
a [`ContextResolver`](https://jax-rs.github.io/apidocs/2.1/index.html?javax/ws/rs/ext/ContextResolver.html).
`ServiceTalkJacksonSerializerFeature` provides a helper method named `contextResolverFor` that
can build a `ContextResolver<JacksonSerializationProvider>` from an `ServiceTalkJacksonSerializerFeature` instance.

It is up to the user to properly register this `ContextResolver` with their application.