# Parkour-AI Trace release gate

Fails the job unless Parkour-AI Trace says the release may go: every item in the release approved and
not changed since, the project's trace chain complete, and every test passed against this commit.

```yaml
- uses: cres-intelligence/trace-gate@v1
  with:
    release: 2.4.0
    token: ${{ secrets.TRACE_GATE_TOKEN }}
    results: build/junit.xml                       # optional: post results first
    results-token: ${{ secrets.TRACE_RESULTS_TOKEN }}
    sbom: build/bom.json                           # optional: post the bill of materials first
    sbom-token: ${{ secrets.TRACE_SBOM_TOKEN }}
```

Tokens come from the project's Settings in Trace. A gate token can only ask; a results token can only
post results; an SBOM token can only post a bill of materials. None can approve anything.
