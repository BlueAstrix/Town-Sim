# Town Sim LLM Starter (Godot 4.3+)

1. Start KoboldCpp with a model loaded (default API: http://localhost:5001).
2. Open this folder in Godot 4.3+ and press F5.
3. Walk around (WASD) and talk to the villagers: Mara, Tobias, Elsie, Finn and Wren.
   Click "End day" to compress every chat into a saved memory.

Files
- data/npcs/*.json  : one file per villager (persona, facts, memories, affection, look)
- data/reply.gbnf   : grammar forcing {say, emotion, affection_delta, topic_flag}
- scripts/kobold_client.gd : autoload HTTP client (change base_url if needed)
- scripts/prompt_builder.gd: assembles dialogue and nightly summary prompts
- scripts/npc.gd    : load/save, clamps LLM output, rolling memories
- scripts/main.gd   : placeholder UI and game loop
- scripts/world.gd  : the village map (MAP), signs (PLACES), NPC placement (NPC_TILES), scrolling camera

NPC progress saves to user:// (Godot: Project > Open User Data Folder). Delete it to reset.

Adding a villager
1. Copy any file in data/npcs/ and edit it (the "look" block sets colours; optional extras:
   apron, bun, long, beard, cap, hat).
2. In scripts/world.gd put a free letter on MAP where they should stand and add it to NPC_TILES.
3. Add the id to NPC_PATHS in scripts/dialogue_ui.gd.
Persona/facts/look are always read from data/npcs/; only memories and affection come from the save.

Next steps: add interiors, portraits keyed by
"emotion", NPC-to-NPC gossip at end of day, schedules, and streaming text.
