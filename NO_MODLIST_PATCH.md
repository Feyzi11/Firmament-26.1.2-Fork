# No-modlist patch

This source tree is Firmament 44.3.0+mc26.1.2 with one local change:

`src/main/kotlin/features/misc/ModAnnouncer.kt` has been replaced with an empty object.

Upstream Firmament's `ModAnnouncer` collected installed Fabric mod IDs and versions on server join and sent them as a `firmament:mod_list` custom payload. This patched source removes the subscription handler and packet code, so rebuilding from this source does not include Firmament's mod-list announcer.

The separately produced patched binary used a compatible no-op class stub so the already-generated subscription table in the original JAR could still load safely. A clean rebuild from this source should regenerate subscriptions without the removed handler.
