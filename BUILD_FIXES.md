# Build fixes in 0.2.1

This revision addresses the JUCE 8 / MSVC compiler errors reported by GitHub Actions:

- Removed the unsupported `juce::TextButton::outlineColourId` reference. JUCE TextButton exposes `buttonColourId`, `buttonOnColourId`, `textColourOffId`, and `textColourOnId`.
- Converted every editor font construction to `juce::Font(juce::FontOptions(typeface, height, styleFlags))`.
- Added an explicit `juce::Justification` to every `Graphics::drawText` call using integer coordinates.
- Made AudioParameterFloat default values explicit `float` literals to avoid narrowing warnings.

The source was checked for remaining instances of the reported invalid API patterns. A successful Windows VST3 build must still be confirmed by the repository's GitHub Actions runner.
