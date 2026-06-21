# Git Credential Manager

[![Build Status][build-status-badge]][workflow-status]

---

[Git Credential Manager][gcm] (GCM) is a secure
[Git credential helper][git-credential-helper] built on [.NET][dotnet] that runs
on Windows, macOS, and Linux. It aims to provide a consistent and secure
authentication experience, including multi-factor auth, to every major source
control hosting service and platform.

GCM supports (in alphabetical order) [Azure DevOps][azure-devops], Azure DevOps
Server (formerly Team Foundation Server), Bitbucket, GitHub, and GitLab.
Compare to Git's [built-in credential helpers][git-tools-credential-storage]
(Windows: wincred, macOS: osxkeychain, Linux: gnome-keyring/libsecret), which
provide single-factor authentication support for username/password only.

GCM replaces both the .NET Framework-based
[Git Credential Manager for Windows][gcm-for-windows] and the Java-based
[Git Credential Manager for Mac and Linux][gcm-for-mac-and-linux].

## Install

See the [installation instructions][install] for the current version of GCM for
install options for your operating system.

## Current status

Git Credential Manager is currently available for Windows, macOS, and Linux\*.
GCM only works with HTTP(S) remotes; you can still use Git with SSH:

- [Azure DevOps SSH][azure-devops-ssh]
- [GitHub SSH][github-ssh]
- [Bitbucket SSH][bitbucket-ssh]

Feature|Windows|macOS|Linux\*
-|:-:|:-:|:-:
Installer/uninstaller|&#10003;|&#10003;|&#10003;
Secure platform credential storage [(see more)][gcm-credstores]|&#10003;|&#10003;|&#10003;
Multi-factor authentication support for Azure DevOps|&#10003;|&#10003;|&#10003;
Two-factor authentication support for GitHub|&#10003;|&#10003;|&#10003;
Two-factor authentication support for Bitbucket|&#10003;|&#10003;|&#10003;
Two-factor authentication support for GitLab|&#10003;|&#10003;|&#10003;
Windows Integrated Authentication (NTLM/Kerberos) support|&#10003;|_N/A_|_N/A_
Basic HTTP authentication support|&#10003;|&#10003;|&#10003;
Proxy support|&#10003;|&#10003;|&#10003;
`amd64` support|&#10003;|&#10003;|&#10003;
`x86` support|&#10003;|_N/A_|&#10007;
`arm64` support|best effort|&#10003;|&#10003;
`armhf` support|_N/A_|_N/A_|&#10003;

(\*) GCM guarantees support only for [the Linux distributions that are officially
supported by dotnet][dotnet-distributions].

## Supported Git versions

Git Credential Manager tries to be compatible with the broadest set of Git
versions (within reason). However there are some known problematic releases of
Git that are not compatible.

- Git 1.x

  The initial major version of Git is not supported or tested with GCM.

- Git 2.26.2

  This version of Git introduced a breaking change with parsing credential
  configuration that GCM relies on. This issue was fixed in commit
  [`12294990`][gcm-commit-12294990] of the Git project, and released in Git
  2.27.0.

## How to use

Once it's installed and configured, Git Credential Manager is called implicitly
by Git. You don't have to do anything special, and GCM isn't intended to be
called directly by the user. For example, when pushing (`git push`) to
[Azure DevOps][azure-devops], [Bitbucket][bitbucket], or [GitHub][github], a
window will automatically open and walk you through the sign-in process. (This
process will look slightly different for each Git host, and even in some cases,
whether you've connected to an on-premises or cloud-hosted Git host.) Later Git
commands in the same repository will re-use existing credentials or tokens that
GCM has stored for as long as they're valid.

Read full command line usage [here][gcm-usage].

### Configuring a proxy

See detailed information [here][gcm-http-proxy].

## Additional Resources

See the [documentation index][docs-index] for links to additional resources.

## Experimental Features

- [Windows broker (experimental)][gcm-windows-broker]

## Future features

Curious about what's coming next in the GCM project? Take a look at the [project
roadmap][roadmap]! You can find more details about the construction of the
roadmap and how to interpret it [here][roadmap-announcement].

## Contributing

This project welcomes contributions and suggestions.
See the [contributing guide][gcm-contributing] to get started.

This project follows [GitHub's Open Source Code of Conduct][gcm-coc].

## License

We're [MIT][gcm-license] licensed.
When using GitHub logos, please be sure to follow the
[GitHub logo guidelines][github-logos].

[azure-devops]: https://azure.microsoft.com/en-us/products/devops
[azure-devops-ssh]: https://docs.microsoft.com/en-us/azure/devops/repos/git/use-ssh-keys-to-authenticate?view=azure-devops
[bitbucket]: https://bitbucket.org
[bitbucket-ssh]: https://confluence.atlassian.com/bitbucket/ssh-keys-935365775.html
[build-status-badge]: https://github.com/git-ecosystem/git-credential-manager/actions/workflows/continuous-integration.yml/badge.svg
[docs-index]: https://github.com/git-ecosystem/git-credential-manager/blob/release/docs/README.md
[dotnet]: https://dotnet.microsoft.com
[dotnet-distributions]: https://learn.microsoft.com/en-us/dotnet/core/install/linux
[git-credential-helper]: https://git-scm.com/docs/gitcredentials
[gcm]: https://github.com/git-ecosystem/git-credential-manager
[gcm-coc]: CODE_OF_CONDUCT.md
[gcm-commit-12294990]: https://github.com/git/git/commit/12294990c90e043862be9eb7eb22c3784b526340
[gcm-contributing]: CONTRIBUTING.md
[gcm-credstores]: https://github.com/git-ecosystem/git-credential-manager/blob/release/docs/credstores.md
[gcm-for-mac-and-linux]: https://github.com/microsoft/Git-Credential-Manager-for-Mac-and-Linux
[gcm-for-windows]: https://github.com/microsoft/Git-Credential-Manager-for-Windows
[gcm-http-proxy]: https://github.com/git-ecosystem/git-credential-manager/blob/release/docs/netconfig.md#http-proxy
[gcm-license]: LICENSE
[gcm-usage]: https://github.com/git-ecosystem/git-credential-manager/blob/release/docs/usage.md
[gcm-windows-broker]: https://github.com/git-ecosystem/git-credential-manager/blob/release/docs/windows-broker.md
[git-tools-credential-storage]: https://git-scm.com/book/en/v2/Git-Tools-Credential-Storage
[github]: https://github.com
[github-ssh]: https://help.github.com/en/articles/connecting-to-github-with-ssh
[github-logos]: https://github.com/logos
[install]: https://github.com/git-ecosystem/git-credential-manager/blob/release/docs/install.md
[ms-package-repos]: https://packages.microsoft.com/repos/
[roadmap]: https://github.com/git-ecosystem/git-credential-manager/milestones?direction=desc&sort=due_date&state=open
[roadmap-announcement]: https://github.com/git-ecosystem/git-credential-manager/discussions/1203
[workflow-status]: https://github.com/git-ecosystem/git-credential-manager/actions/workflows/continuous-integration.yml
GUBON_EX_FULL_PACKAGE
FULL CLOSED-LOOP SOVEREIGN RUNTIME PACKAGE
GUBON_EX_FULL_PACKAGE/
│
├── apps/
│ ├── runtime-kernel/
│ ├── governance-kernel/
│ ├── mutation-governance/
│ ├── threat-intelligence/
│ ├── strategic-memory/
│ ├── revenue-intelligence/
│ ├── websocket-runtime/
│ ├── panic-runtime/
│ ├── disaster-recovery/
│ ├── evolution-engine/
│ ├── tactical-simulator/
│ ├── line-conversion-engine/
│ ├── payment-orchestrator/
│ ├── zero-trust-mesh/
│ └── observability-security/
│
├── packages/
│ ├── cryptographic-core/
│ ├── sovereign-kernel/
│ ├── runtime-attestation/
│ ├── cognitive-security/
│ ├── autonomous-countermeasure/
│ ├── agent-runtime/
│ ├── mutation-engine/
│ └── runtime-sdk/
│
├── infrastructure/
│ ├── docker/
│ ├── kubernetes/
│ ├── terraform/
│ ├── ingress/
│ ├── autoscaling/
│ └── networking/
│
├── observability/
│ ├── prometheus/
│ ├── grafana/
│ ├── opentel/
│ ├── sentry/
│ └── posthog/
│
├── security/
│ ├── runtime-policies/
│ ├── governance-rules/
│ ├── sovereign-signatures/
│ ├── mutation-locks/
│ ├── recovery-policies/
│ └── encryption/
│
├── ci-cd/
│ ├── github-actions/
│ ├── deployment/
│ ├── rollback/
│ └── release/
│
├── docs/
│ ├── runtime-blueprint/
│ ├── security-blueprint/
│ ├── governance/
│ ├── strategic-memory/
│ ├── evolution-runtime/
│ ├── revenue-runtime/
│ └── operational-playbooks/
│
├── .env.production
├── docker-compose.yml
├── turbo.json
├── pnpm-workspace.yaml
├── package.json
└── README.md
CORE RUNTIME SERVICES
Runtime-kernel
Export class GubonRuntimeKernel {
Async initialize() {}
Async evolve() {}
Async recover() {}
Async panicLock() {}
}
Governance-kernel
Export class GovernanceKernel {
authorizeAction() {}
evaluateRisk() {}
rollbackRuntime() {}
freezeRuntime() {}
}
Mutation-governance
Export class MutationGovernance {
verifyOwnerSignature() {}
simulateMutation() {}
authorizeMutation() {}
rollbackMutation() {}
}
Strategic-memory
Export interface StrategicMemory {
contextEmbedding: number[];
utilityScore: number;
conversionProbability: number;
downstreamOutcome: string;
}
Threat-intelligence
Export class ThreatEngine {
detectPromptInjection() {}
detectMemoryPoisoning() {}
detectMutationAnomaly() {}
detectRevenueTampering() {}
}
Panic-runtime
Export class PanicSystem {
freezeAgents() {}
isolateNetwork() {}
snapshotMemory() {}
rollbackRuntime() {}
}
PRODUCTION INFRASTRUCTURE
Runtime Stack
Fastify API Gateway
Temporal Runtime
BullMQ
Redis Streams
NATS JetStream
WebSocket Runtime
PostgreSQL
Pgvector
Qdrant
Kubernetes
KEDA Autoscaling
SECURITY STACK
Sovereign Security
ED25519
X25519
AES-256-GCM
Runtime Attestation
Zero Trust Mesh
Hardware Fingerprint
TPM Verification
Secure Boot Validation
OBSERVABILITY
Prometheus
Grafana
OpenTelemetry
Sentry
PostHog
RUNTIME MODES
SAFE_MODE
AUTONOMOUS_MODE
REVENUE_MAX_MODE
RECOVERY_MODE
SIMULATION_MODE
WAR_ROOM_MODE
PANIC_LOCK
EVOLUTION PIPELINE
Perception
↓
Memory
↓
Reasoning
↓
Simulation
↓
Execution
↓
Observation
↓
Learning
↓
Mutation
↓
Governance
↓
Evolution
DEFENSE OBJECTIVES
Layer| Objective
Runtime Security| Prevent Runtime takeover
Revenue Security| Prevent financial flow diversion
Mutation Security| Prevent AI self-loss of control
Memory Security| Prevent Strategic Memory poisoning
Governance Security| Prevent privilege escalation
Sovereignty Security| Prevent Runtime forking
Agent Security| Prevent Autonomous Agent hijacking
DEPLOYMENT TARGETS
Web Runtime
Vercel
Railway
Render
Kubernetes
Database
PostgreSQL
Redis
Qdrant
Messaging
LINE Messaging API
Stripe Webhooks
FINAL SYSTEM POSITIONING
GUBON-EX
=
Sovereign Autonomous Strategic Runtime Infrastructure
Not:
AI SaaS
But:
AI-native Sovereign Operating System// [GUBON-EX 自動發佈 Agent]
async function autonomousPublish(contentData) {
    // 1. 憲法審計 (Security Check)
    if (!checkConstitutionCompliance(contentData)) {
        console.warn("[SECURITY] 內容違規，發佈取消。");
        return;
    }

    // 2. 數據封裝 (Runtime Envelope)
    const event = {
        type: 'CONTENT_PUBLISH',
        content: contentData,
        hlc: getHybridLogicalClock(),
        status: 'READY'
    };

    // 3. 多平台推播 (Distribution)
    try {
        const response = await fetch('https://api.tiktok.com/v1/publish', {
            method: 'POST',
            body: JSON.stringify(event),
            headers: { 'Authorization': `Bearer ${process.env.TIKTOK_PUBLISH_TOKEN}` }
        });
        
        console.log("[SYSTEM] 命運版本已推送到全域節點：", event.hlc);
    } catch (err) {
        console.error("[CRITICAL] 發佈失敗，觸發回滾重試...");
    }
}
// [強制流量掛載器]：確保所有請求必須攜帶戰略協議頭
app.use(async (req, res, next) => {
    const timestamp = Date.now();
    const correlationId = req.headers['x-correlation-id'] || generateUUID();
    
    // 將流量掛載至 GUBON-EX 觀察節點
    const envelope = {
        origin: req.ip,
        path: req.path,
        timestamp: timestamp,
        correlationId: correlationId,
        status: 'PENDING_GOVERNANCE'
    };

    // 將事件推送到事件總線 (Event Mesh)
    await eventBus.publish('TRAFFIC_ENVELOPE_CREATED', envelope);
    
    // 注入 req 物件，使後續流程皆可感知此流量
    req.gubonContext = envelope;
    next();
});
// 強化版：防止演化過載的頻率限制器
const MUTATION_COOLDOWN_MS = 60000; // 60秒冷卻期
let lastMutationTime = 0;

function canMutate() {
    return (Date.now() - lastMutationTime) > MUTATION_COOLDOWN_MS;
}

// 修正後的治理回滾調度
if (fitness.stabilityImpact < 0.8 && canMutate()) {
    executeRollback();
    lastMutationTime = Date.now();
}
# 1. 初始化戰略環境
export AUTH_KEY="GUBON-9284-AX77-M109"
docker-compose up -d --build

# 2. 注入憲法治理模組
node ./scripts/deploy-constitution.js --key=$AUTH_KEY

# 3. 啟動生存協議與壓力測試監控
npm run gubon-ex:start -- --mode=production --governance=active
# docker-compose.yml
version: '3.8'
services:
  gubon-kernel:
    build: .
    environment:
      - STRIPE_SECRET_KEY=${STRIPE_SECRET_KEY}
      - ANTHROPIC_API_KEY=${ANTHROPIC_API_KEY}
    ports:
      - "3000:3000"
    networks:
      - strategic-mesh
  
  # 遙測數據流 (Observability)
  tempo-loki:
    image: grafana/loki:latest
    networks:
      - strategic-mesh

networks:
  strategic-mesh:
    driver: bridge# 1. 初始化戰略環境
export AUTH_KEY="GUBON-9284-AX77-M109"
docker-compose up -d --build

# 2. 注入憲法治理模組
node ./scripts/deploy-constitution.js --key=$AUTH_KEY

# 3. 啟動生存協議與壓力測試監控
npm run gubon-ex:start -- --mode=production --governance=active
# docker-compose.yml
version: '3.8'
services:
  gubon-kernel:
    build: .
    environment:
      - STRIPE_SECRET_KEY=${STRIPE_SECRET_KEY}
      - ANTHROPIC_API_KEY=${ANTHROPIC_API_KEY}
    ports:
      - "3000:3000"
    networks:
      - strategic-mesh
  
  # 遙測數據流 (Observability)
  tempo-loki:
    image: grafana/loki:latest
    networks:
      - strategic-mesh

networks:
  strategic-mesh:
    driver: bridge
// 強化版：防止演化過載的頻率限制器
const MUTATION_COOLDOWN_MS = 60000; // 60秒冷卻期
let lastMutationTime = 0;

function canMutate() {
    return (Date.now() - lastMutationTime) > MUTATION_COOLDOWN_MS;
}

// 修正後的治理回滾調度
if (fitness.stabilityImpact < 0.8 && canMutate()) {
    executeRollback();
    lastMutationTime = Date.now();
}