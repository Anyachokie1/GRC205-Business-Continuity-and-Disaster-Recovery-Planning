# **GRC205** **BUSINESS CONTINUITY AND DISASTER RECOVERY ASSIGNMENT**

**Student Name:** Faith Anyachokie  
**Student ID:** 2025/GCR/12676  
**Module:** GRC205 – Incident Management & Business Continuity  
**Date:** 23/10/2026

# 

# **Task 1: Business Impact Analysis**

## **1.1 Five-function BIA**

Tables 1 and 2 record the BIA for F1 to F5, following the approach in [(NIST, 2010\)](https://csrc.nist.gov/pubs/sp/800/34/r1/upd1/final). Owner roles are fictional titles. Impact is shown for the first 8 hours, 8 to 24 hours and 24 to 72 hours; the supplied rates cover the first 24 hours and later impact is qualitative. Each minimum acceptable service (MAS) names the controls that make a manual process safe. Impact steps up as deadlines pass: F1 loses value at 11:00, F2 at 16:00, F3 at 18:00 and F4 at 12:00 on Day 1, while F5 matters only after 48 hours, which is why the urgency of each minimum service differs.

***Table 1: BIA profile***

| Function | Owner role | Users affected | Critical resources | Dependencies |
| :---- | :---- | :---- | :---- | :---- |
| **F1 Teaching and assessment** | Head of Assessment | 1,800 learners; 120 sitting the 11:00 exam (40 need centre workstations, 80 own devices); teaching and invigilation staff | Systems: LMS01, DB01. People: examinations officer, invigilators, 2 technicians. Premises: alternate facility (25 workstations from 10:00). Suppliers: alternate facility, mobile ISP, Microsoft 365\. Information: exam papers, candidate list, access arrangements, submission records. | Recovery network, AUTH01, DB01, LMS01; staff, secure access, communication. |
| **F2 Fees and finance** | Finance Manager | Fee-paying learners; finance staff | Systems: FIN01, DB01. People: finance officers (dual control). Premises: alternate facility or remote working. Suppliers: external payment provider, bank. Information: fee ledger, wallet records, receipts, provider transaction reports. | Recovery network, AUTH01, DB01, FIN01; staff, secure access, communication. |
| **F3 Admissions and registration** | Registrar | Applicants, new and continuing learners, registry staff | Systems: REG01, DB01. People: registry officers. Premises: remote or alternate facility. Suppliers: Microsoft 365 (temporary forms). Information: application forms, registration change requests, closing list. | Recovery network, AUTH01, DB01, REG01; staff, secure access, communication. |
| **F4 Staff payroll** | HR and Payroll Manager | 90 staff; HR and finance staff | Systems: HR01, DB01. People: HR officer, finance approver. Premises: remote or alternate facility. Suppliers: bank (file due 12:00 Day 1). Information: salary master data, approved changes, last approved payroll file. | Recovery network, AUTH01, DB01, HR01; staff, secure access, communication. |
| **F5 Records and certificates** | Records Officer | Learners and alumni requesting records; records staff | Systems: FS01. People: records officer. Premises: remote or alternate facility. Suppliers: offsite backup provider. Information: record and certificate files, access control lists. | Recovery network, AUTH01, FS01; staff, secure access, communication. |

***Table 2: BIA impact and minimum service***

| Function | 0 to 8 h | 8 to 24 h | 24 to 72 h | Minimum acceptable service and controls | Rank |
| :---- | :---- | :---- | :---- | :---- | :---- |
| **F1** | Examination at risk; no assessment service. NGN 480,000 (plus NGN 120,000 if no acceptable service by 11:00). | Cumulative NGN 1,440,000; teaching and further assessments cancelled; integrity doubts. | Progression decisions delayed; welfare and reputation harm grow. | Temporary Microsoft 365 assessment for 25 centre seats and own devices; Examinations Officer approves papers; ID check and invigilation; submissions logged in a register; results held until reconciled. | 1 |
| **F2** | Fee confirmation due 16:00 at risk. NGN 320,000. | Cumulative NGN 960,000; receipts and wallets stale; reconciliation backlog. | Disputed payments, duplicate charges, complaints. | Provider portal is source of truth; manual receipt register with dual entry and supervisor approval; reconcile to provider report. | 2 |
| **F3** | Admissions close 18:00; applications cannot be entered. NGN 160,000. | Cumulative NGN 480,000; applicants lost if the window is missed. | Registration changes pile up; enrolment errors. | Timestamped online form capture; Registrar approves; later duplicate-checked import. | 3 |
| **F4** | No immediate failure; deadline 12:00 Day 1\. NGN 80,000. | Cumulative NGN 240,000; payroll risk rises as deadline nears. | Late or wrong pay harms staff and needs manual correction. | Prior approved payroll plus change log; two-person approval (HR and Finance); one bank submission with duplicate check. | 4 |
| **F5** | 48-hour commitment not yet breached. NGN 40,000. | Cumulative NGN 120,000; request queue grows. | Commitment breached after 48 h; integrity and access risk if unverified files are served. | Log requests, verify identity, release only validated documents; keep file access restricted. | 5 |

## **1.2 Impact calculations**

Each function's cost is its hourly rate multiplied by the hours of disruption, assuming no recovery or continuity measures. The combined hourly rate is NGN 135,000. The 11:00 examination falls three hours after the disruption, so with no acceptable assessment service, the one-off NGN 120,000 rescheduling cost applies once in each window. The 8-hour total is NGN 1,080,000 \+ 120,000 \= NGN 1,200,000, and the 24-hour total is NGN 3,240,000 \+ 120,000 \= NGN 3,360,000 (Table 3).

***Table 3: Disruption cost calculations (NGN)***

| Function | Rate per hour | 8-hour calculation | 8-hour cost | 24-hour calculation | 24-hour cost |
| :---- | :---- | :---- | :---- | :---- | :---- |
| F1 Teaching and assessment | 60,000 | 60,000 × 8 | 480,000 | 60,000 × 24 | 1,440,000 |
| F2 Fees and finance | 40,000 | 40,000 × 8 | 320,000 | 40,000 × 24 | 960,000 |
| F3 Admissions and registration | 20,000 | 20,000 × 8 | 160,000 | 20,000 × 24 | 480,000 |
| F4 Staff payroll | 10,000 | 10,000 × 8 | 80,000 | 10,000 × 24 | 240,000 |
| F5 Records and certificates | 5,000 | 5,000 × 8 | 40,000 | 5,000 × 24 | 120,000 |
| **Subtotal (hourly costs)** | **135,000** | 135,000 × 8 | **1,080,000** | 135,000 × 24 | **3,240,000** |
| Examination rescheduling (one-off; 11:00 trigger met) |  | Added once | 120,000 | Added once | 120,000 |
| **Combined total** |  | 1,080,000 \+ 120,000 | **1,200,000** | 3,240,000 \+ 120,000 | **3,360,000** |

Two limitations apply. First, constant hourly rates treat every hour alike, yet losses cluster at deadlines (the 11:00 examination, fees at 16:00, admissions at 18:00), so the true cost curve is stepped and a fixed rate can over- or understate any window. Second, the figures are exercise estimates of incremental disruption only: they exclude recovery spend, refunds, penalties, insurance and later catch-up effort, and they assume no mitigation. Financial impact must also be kept separate from learner welfare (missed assessments, stress, delayed progression), reputation (trust among learners, sponsors and accreditors) and data integrity (wrong fee, payroll or record data that causes harm long after systems return). These carry no naira value here, yet they can outrank money, for example by holding examination results until marks are reconciled.

## **1.3 Priorities and dependency risks**

Business priority follows deadlines and harm: F1 first (11:00 examination and assessment integrity), then F2 (16:00), F3 (18:00), F4 (12:00 on Day 1\) and F5 (48-hour commitment). The technical restoration order differs because F1 to F4 all need the recovery network, AUTH01 and DB01 before their applications start: network, AUTH01, security and backup checks, DB01, then LMS01, FIN01, REG01 and HR01, with FS01 restored in parallel once AUTH01 and the checks are complete. DB01 cannot be bypassed and LMS01 cannot return before 11:45 in the baseline, so the 11:00 examination is protected by a continuity workaround, not by restoration order. Important dependency risks are:

* DB01 is a single shared dependency for four functions; a failed restore stops F1 to F4 together.

* Production and network backup administration share one identity, so one compromised account could alter or delete backups and production data; the offsite provider's access independence is undocumented.

* AUTH01 is 8 hours old and sits behind the network and security checks, so a late or failed directory restore delays every function.

* Only two technicians are available, creating key-person and fatigue risk, especially if the outage is extended.

* The alternate facility's 25 workstations and mobile-internet access to Microsoft 365 are untested single points for the examination.

# 

# **Task 2: Recovery Objectives and Backup Design**

## **2.1 Definitions and targets**

Recovery Time Objective (RTO) is the target time within which a function must be restored to a defined service level. Recovery Point Objective (RPO) is the maximum acceptable age of recoverable data, measured back from the disruption. Maximum Tolerable Downtime (MTD) is the longest disruption the business can bear before harm becomes unacceptable (ICDFA, n.d.). Targets in Table 4 are commitments to be tested, not guarantees. Each RTO sits well inside its MTD to leave a buffer for acceptance testing, reconciliation and one failed restore step. Recovery is declared per function only at the minimum service level: the application restored, authenticating through AUTH01, data checked against the checkpoint, and accepted by the function owner. Technical restoration alone is not a declaration. Targets for F3 to F5 are looser than for F1 and F2 because their deadlines are later and their data can be rebuilt from other sources.

***Table 4: Recovery objective matrix***

| Function | MTD | RTO (declared when) | RPO | Basis and buffer |
| :---- | :---- | :---- | :---- | :---- |
| **F1** | 8 h | 4 h: LMS01 restored and accepted. Interim: acceptable assessment service by 3 h (11:00) through the workaround. | 1 h | MTD is the end of the Day 0 working period (16:00). The 4-hour buffer (50% of MTD) covers acceptance testing and one failed step. The 11:00 examination sits at 3 h, so it is covered by the workaround. |
| **F2** | 8 h | 5 h: FIN01 restored; receipts reconciled to provider report. | 1 h | Fee confirmation is due at 16:00. The 3-hour buffer leaves time for provider reconciliation. |
| **F3** | 10 h | 6 h: REG01 restored and accepted. | 4 h | Admissions close at 18:00. Applications since the checkpoint can be re-captured from email and forms; 4-hour buffer. |
| **F4** | 24 h | 8 h: HR01 restored; payroll data verified. | 4 h | Bank file due 12:00 on Day 1 (28 h). MTD of 24 h leaves 4 h for approvals; changes can be re-applied from the HR change log. |
| **F5** | 48 h | 24 h: FS01 restored with access controls checked. | 8 h | Matches the 48-hour service commitment; 24-hour buffer; changes within a working day can be rebuilt from request logs. |
| **Shared platform** | n/a | Network 1 h; AUTH01 2 h; DB01 3.5 h. | DB01 1 h; AUTH01 4 h | Set by the tightest dependent function (F1) so applications can restore within 4 h. |

## **2.2 Checkpoint analysis**

At 08:00 the latest recoverable DB01 point is the 07:00 incremental (B02), so its age is 08:00 − 07:00 \= 1 hour, provided B01 and every incremental to 07:00 restore. AUTH01 (B03, 00:00) is 8 hours old and FS01 (B04, 23:00 on Day −1) is 9 hours old. The disconnected full backup from 17:00 on Day −3 is 63 hours old (72 hours less 9 hours). Table 5 maps these windows to RPOs. DB01 meets the F1 to F4 targets, but with no margin for F1 and F2: one bad incremental moves the recovery point back by an hour or more. AUTH01 breaches the 4-hour shared target by 4 hours and FS01 breaches the F5 target by 1 hour. Data created after each checkpoint can partly be reconciled from temporary records: payments from provider reports, and applications and requests from email and forms. Local receipts and wallet updates not mirrored by the provider, examination work held only locally, directory changes after 00:00, record changes after 23:00 and any transaction in flight at 07:00 cannot be assumed recoverable.

***Table 5: Checkpoint ages and RPO comparison***

| Checkpoint | Data point (WAT) | Age at 08:00 | Functions affected | RPO | Result |
| :---- | :---- | :---- | :---- | :---- | :---- |
| **DB01: B01 full plus B02 incrementals** | 07:00 Day 0 | 1 h (08:00 − 07:00) | F1 to F4 | F1 1 h; F2 1 h; F3 4 h; F4 4 h | Met; zero margin for F1 and F2 |
| **AUTH01: B03 snapshot** | 00:00 Day 0 | 8 h (08:00 − 00:00) | All five functions | 4 h | Breach of 4 h |
| **FS01: B04 full** | 23:00 Day −1 | 9 h (08:00 − 23:00) | F5 | 8 h | Breach of 1 h |
| **Disconnected full backup** | 17:00 Day −3 | 63 h (72 h − 9 h) | Last-resort fallback | n/a | Outside every RPO |

## **2.3 Backup and restoration design**

Table 6 closes the gaps. DB01 keeps a nightly full backup, 4-hourly differentials and hourly incrementals. AUTH01 is snapshotted every 4 hours and after directory changes. FS01 gets a nightly full plus incrementals at 07:00 and 15:00, so no copy is older than 8 hours. The exact chain to restore DB01 to 07:00 is B01 (full, 23:00 Day −1) plus every incremental from 00:00 to 07:00, applied in order (eight files if hourly, assumption A1). A 07:00 differential gives a shorter second route: B01 plus that differential. The 3-2-1 principle is met with three copies (production, local backup, offsite provider) on two media types with one offsite, plus an immutable or offline copy held under a separate administrator identity. Access is restricted by multi-factor authentication and two-person approval for deletion; copies are encrypted with keys escrowed outside AUTH01, and restores are tested monthly for integrity and quarterly in full. Retention lets us step back past a corrupted or maliciously changed backup, which matters because the most recent restore point may already contain the damage.

Offsite storage or a live replica alone does not establish recoverability. An offsite copy may be incomplete, corrupt, impossible to decrypt, or deletable with the same compromised credentials, and a replica copies corruption or malicious changes within minutes. Recoverability is proven only by restoring in isolation within the RTO. Integrity is checked by hash and catalogue verification, chain completeness, malware scanning and a test restore. Access independence is checked by showing that production and network administrator credentials cannot read, change or delete the immutable and offsite copies, and by obtaining the provider's documented controls. Usability is checked by record counts, last-transaction timestamps and owner sample tests. Unverified assumptions are labelled in Appendix A.

***Table 6: Backup schedule and restoration design***

| Item | Schedule and type | Retention (proposed) | Placement | Protection and testing |
| :---- | :---- | :---- | :---- | :---- |
| **DB01** | Full nightly 23:00; differential every 4 h; incremental hourly. | Daily 14 days; weekly 8 weeks; monthly 6 months. | Local backup; offsite provider; immutable copy of the nightly full. | Hash check every job; chain completeness check; quarterly isolated chain restore. |
| **AUTH01** | Snapshot every 4 h and after directory changes; configuration export. | 14 days. | Local; offsite; immutable weekly copy. | Quarterly restore test; keys held outside AUTH01. |
| **FS01** | Full nightly 23:00; incrementals 07:00 and 15:00. | Daily 14 days; monthly 12 months (subject to records policy). | Local; offsite; immutable weekly copy. | Access control lists compared after restore; checksum sample. |
| **Independent copy** | Weekly full of DB01, AUTH01 and FS01 to offline or object-lock storage. | 8 weeks. | Separate tenant or offline media. | Separate credentials; quarterly access-independence test. |
| **DB01 restore chain** | B01 \+ incrementals 00:00 to 07:00 in order; alternative B01 \+ 07:00 differential. | Not applicable. | Both routes held offsite. | Chain verified complete before restore starts. |

## 

# **Task 3: Recovery Strategy and Budget**

## **3.1 Options, budget and recommendation**

Table 7 itemises each package with the two required additions, and Table 8 compares the options against the Task 2 targets. All three fit the NGN 3,000,000 limit, but Hot uses all of it and leaves no contingency. Cold, with 24 to 48 hours to first service and up to 24 hours of data loss, fails every RTO and RPO and cannot protect the F4 bank deadline. Hot, at about 1 hour and up to 15 minutes, meets every objective on paper, but it consumes the whole limit, depends heavily on one supplier, and a live replica copies corruption or malicious changes, so it still needs the independent backups.

***Table 7: Itemised annual cost (NGN)***

| Package | Annual base | Independent protected backups | Training and tests | Annual total | Within 3,000,000? | Headroom |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| **Cold** | 600,000 | 400,000 | 200,000 | **1,200,000** | Yes | 1,800,000 |
| **Warm** | 1,500,000 | 400,000 | 200,000 | **2,100,000** | Yes | 900,000 |
| **Hot** | 2,400,000 | 400,000 | 200,000 | **3,000,000** | Yes, exactly at the limit | 0 |

***Table 8: Option comparison***

| Criterion | Cold | Warm | Hot |
| :---- | :---- | :---- | :---- |
| **First critical service vs F1 RTO of 4 h** | 24 to 48 h: fails | 3 to 5 h: meets only in lower half; drill gives 3 h 45 min | About 1 h: meets |
| **Data loss vs RPO (F1/F2 1 h; F3/F4 4 h; F5 8 h)** | Up to 24 h: fails all | 1 to 6 h: F1 and F2 at risk; F3 and F4 likely met | Up to 15 min: meets all |
| **Staffing (two technicians)** | Rebuild over days; two technicians cannot cover it. | Two technicians reach 12:15 in the drill; fatigue beyond a day. | Fewest manual steps; validation staff still needed. |
| **Geography** | Offsite only; slowest return. | Warm site must be outside the flood zone (to validate). | Replica site must be independent of the main site (to validate). |
| **Supplier dependency** | Backup provider. | Warm site and backup providers. | Highest: replication and hot-site provider. |
| **Corruption or malicious-change risk** | Low propagation; data stale. | Medium; restore from a validated point. | High: replica copies bad changes; needs independent backups. |
| **Annual cost / headroom** | 1,200,000 / 1,800,000 | 2,100,000 / 900,000 | 3,000,000 / 0 |

I recommend Warm at NGN 2,100,000, leaving NGN 900,000 unallocated as contingency. Its 3 to 5 hour estimate meets the F1 RTO of 4 hours only in the lower half of the range, but the modelled drill gives LMS01 at 3 hours 45 minutes and all functions by 12:15. Warm cannot meet three objectives unaided. It cannot deliver the 3-hour interim assessment service, so the Microsoft 365 workaround is essential. Its 1 to 6 hour data-loss window cannot guarantee the 1-hour RPO for F1 and F2 unless the contract or my hourly backup design delivers it. The upper 5-hour estimate would breach the F1 RTO. Residual risks are the untested package timings, supplier dependency, the geography of the alternate facility, and dependence on two technicians. The Institute Director must accept them, with the Finance Manager confirming the budget and the Technical Recovery Lead and IR Lead advising. Choosing Warm accepts slower recovery than Hot in exchange for NGN 900,000 of headroom, less supplier lock-in and a design that does not copy bad changes in real time.

## **3.2 Cost against impact and evidence**

The recommended cost of NGN 2,100,000 compares with unmitigated single-outage estimates of NGN 1,200,000 (8 hours) and NGN 3,360,000 (24 hours). A single outage cannot establish annual return on investment, because return depends on how often outages occur, how long they last, what share of loss each package avoids, and what else is spent. Annual benefit is frequency multiplied by avoided loss, less annual cost. Before approving spend or accepting supplier claims, I would require flood and power-failure frequency data, a witnessed test of package timings, contractual service levels with remedies, the provider's access-independence documentation and financial standing, confirmation that the warm site is outside the flood zone, insurance terms, and function owners' validation of the impact rates.

# **Task 4: Business Continuity and Disaster Recovery Plan**

## **4.1 Scope, activation and coordination**

**Scope.** All five functions, the recovery network, AUTH01, DB01, FS01 and the four applications, covering 1,800 learners and 90 staff, for a site loss of up to five days. **Activation.** The plan is activated when the site or core systems are unavailable and expected to stay so for more than 4 hours, when any function is expected to breach its MTD, or when a deadline-bound service (examination, fees, admissions, payroll) cannot run. The Institute Director is the authorised decision maker; the Head of Academic Operations is deputy if the Director cannot be reached within 15 minutes. **Escalation.** Any duty officer informs the Coordinator, who escalates to the Director within 15 minutes of a threshold being met.

**Communication.** Contact roles are kept on a call tree stored in Microsoft 365 and on printed cards. Primary channels are Microsoft 365 email and Teams over mobile internet; bulk SMS and the phone tree are the alternative. Situation reports (SITREPs) go to the Director hourly until 14:00 on Day 0, then every 4 hours and at each deadline. Each SITREP states service status by function, checkpoint and data-loss window, deadlines at risk, decisions needed and the next report time. **Teamwork.** One coordination cell, led by the Coordinator, joins four teams: continuity (temporary services), technical recovery (the two technicians), facilities (site safety and the alternate venue) and incident response (compromise screening). No team restores over suspect data until incident response clears it, and facilities must clear any re-entry.

***Table 9: RACI matrix***

| Activity | ID | CO | TL | TECH | FM | IR | BO | COM |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| 1 Plan activation and declaration | **A** | R | C | I | C | C | I | I |
| 2 Temporary assessment delivery | I | R | C | R | C | C | **A/R** | I |
| 3 Backup selection and validation | I | I | **A/R** | R |  | C |  |  |
| 4 Restoration and technical validation | I | C | **A/R** | R |  | C | C | I |
| 5 Business acceptance of restored service | I | C | C |  |  |  | **A/R** | I |
| 6 Stakeholder communication | C | C | I |  | I | C | C | **A/R** |
| 7 Suspected compromise triage and containment | I | R | R | R |  | **A/R** | I | C |
| 8 Return to primary site and sign-off | **A** | R | R | R | R | C | R | I |

Roles: ID Institute Director (deputy: Head of Academic Operations); CO BC/DR Coordinator; TL Technical Recovery Lead; TECH technicians; FM Facilities Manager; IR Incident Response Lead; BO function owners; COM Communications Lead. A accountable, R responsible, C consulted, I informed.

## **4.2 Temporary procedures**

The 25 centre workstations (from 10:00) cannot seat all 40 learners who need one. Twenty-five sit at 11:00, with first priority for learners with accessibility adjustments; the other 15 sit in a second sitting once seats are reset, on an equivalent form, supervised between sittings to protect integrity. The 80 own-device learners sit at 11:00, identified by Microsoft 365 sign-in and invigilated. The Examinations Officer approves papers and seating plans. Table 10 sets out procedures for F1 to F5. Minimum staffing is the two technicians, the Coordinator, the Examinations Officer, two invigilators per room, two finance staff for dual control, one registry officer, one HR officer, one records officer, the Facilities Manager, a communications lead and the IR lead on call. Minimum equipment is the 25 workstations, mobile hotspots, power strips and printed rosters. Supplier support is needed from the alternate facility, mobile ISP, Microsoft 365, payment provider, bank and offsite backup provider.

***Table 10: Temporary procedures***

| Function | Temporary procedure | Approvals and integrity controls | Accessibility, privacy and records | Later reconciliation |
| :---- | :---- | :---- | :---- | :---- |
| **F1** | Run the examination through a temporary Microsoft 365-based assessment: 25 centre seats and 80 own devices at 11:00; remaining 15 learners in a second sitting. | Examinations Officer approves papers and seating; sign-in ID check; invigilators; second-sitting candidates supervised; submissions logged. | Adjustments first; candidate data limited to named staff; Northbridge accounts only; attendance register. | Compare submissions with the register; load marks into LMS01 only after acceptance; hold results until reconciled. |
| **F2** | Use the provider portal as source of truth; record fees in a controlled receipt register. | Dual entry; supervisor approves each batch; confirm to provider by 16:00 only from reconciled totals. | Register restricted to finance staff; no card data stored; dated exports kept. | After FIN01 acceptance, post register entries; match to provider reports; clear differences. |
| **F3** | Capture applications and registration changes through timestamped online forms until 18:00; log email requests. | Registrar approves cut-off and exceptions; numbered log. | Mobile-friendly forms; personal data in a restricted library; privacy notice. | Import after REG01 acceptance with duplicate checks; match form count to records. |
| **F4** | Prepare payroll from the last approved file plus change log; no starters or bank changes without verification. | HR Manager and Finance Manager approve; one bank submission; duplicate check. | Restricted payroll workspace; approval evidence kept. | Compare with restored HR01 before 12:00 on Day 1; correct any difference in the next cycle. |
| **F5** | Log record and certificate requests; verify identity; release only from validated sources. | Records Officer approves release; second check for certificates. | Access limited to records staff; encrypted attachments; request log. | Check log against FS01 after acceptance; confirm no request missed inside 48 h. |

## **4.3 DR runbook**

Table 11 is the ordered runbook. Restoring technology means a system passes technical validation. Resuming an acceptable business service also needs the function owner's acceptance, reconciliation of the checkpoint gap and clear manual controls for outstanding work. Each function therefore carries two timestamps: restored and resumed. If acceptance fails or corruption appears later, rollback disables the service, returns the function to its temporary procedure and preserves the failed state for investigation.

***Table 11: DR runbook***

| Step | Action | Prerequisite | Owner | Completion check | If the step fails |
| :---- | :---- | :---- | :---- | :---- | :---- |
| **R1** | Confirm activation; screen for compromise indicators. | Director declaration | CO, IR | Incident log open; no unresolved indicators. | Treat as security incident; IR leads; restore only from IR-cleared copies. |
| **R2** | Select backup set: B01 plus incrementals to 07:00, B03, B04. | R1 | TL | Catalogue shows complete chain; checkpoint times recorded. | Use latest valid point; disconnected full only as last resort; record data-loss window. |
| **R3** | Recover network (30 min). | R2 | TECH T1 | Links, DNS and routing up; Microsoft 365 reachable. | Use second ISP or hotspots; escalate to supplier. |
| **R4** | Restore AUTH01 (30 min). | R3 | TECH T1 | Test logons for admin and sample user; admin accounts reviewed. | Rebuild from configuration; use Microsoft 365 identity and manual access list. |
| **R5** | Security and backup checks (30 min). | R4 | TECH T1, IR | Hash and catalogue verified; malware scan clean; keys available outside AUTH01. | Stop; IR decides; switch to alternative chain or independent copy. |
| **R6** | Restore DB01: B01 plus incrementals (90 min). | R5 | TECH T1 | Consistency check passes; last transaction 07:00; record counts within tolerance. | Fall back to last valid increment; restate data-loss window; use independent copy if B01 fails. |
| **R7** | Restore FS01 (60 min). | R4, R5 | TECH T2 | Access control lists match; checksum sample passes. | Serve requests manually; restore from older copy. |
| **R8** | Restore LMS01, FIN01, REG01, HR01 as scheduled. | R6 | TECH T1, T2 | Application starts; login via AUTH01; sample transactions; totals tie to counts. | Keep temporary procedure; retry from snapshot; call supplier. |
| **R9** | Business acceptance. | R7, R8 | BO | Owner samples data, reconciles checkpoint gap and signs. | Continue manual service; fix and retest. |
| **R10** | Declare each function resumed; close temporary controls. | R9 | CO | Director informed; users notified; reconciliation task opened. | Hold function in "restored, not resumed" state. |
| **R11** | Rollback. | Failed acceptance or corruption found | TL, IR | Service disabled; users return to manual procedure; failed state preserved. | Restore from alternate point; repeat R6 to R9. |

## **4.4 Communication, compromise and safe return**

Table 12 is the stakeholder communication matrix. The initial learner notice follows.

***Table 12: Communication matrix***

| Stakeholder | Information needed | Channel | Owner | Timing |
| :---- | :---- | :---- | :---- | :---- |
| **Learners (1,800)** | Site status, examination arrangements, fees, admissions, support contacts. | Microsoft 365 email; bulk SMS; website notice. | COM | Within 60 min of activation; every 4 h and at deadlines. |
| **Staff (90)** | Work locations, roles, instructions. | Teams; phone tree. | CO | Within 30 min; hourly summary. |
| **Examination candidates and invigilators** | Venue, seating, ID and device rules. | Email; Teams. | Examinations Officer | Before 09:30 and again before 10:30. |
| **Director and governing board** | SITREPs, decisions, cost and risk. | Email; phone. | CO | Hourly to 14:00; then every 4 h. |
| **Payment provider and bank** | Fee and payroll status; reconciliation needs. | Phone; email. | Finance Manager | Before 16:00 on Day 0; before 12:00 on Day 1\. |
| **Alternate facility** | Seats, access, extended hours. | Phone. | FM | At activation and 10:00. |
| **Backup provider and Microsoft 365** | Access requests; restore support. | Support line. | TL | At activation. |
| **Regulators, accreditors, data protection authority** | Material impact or personal data incident. | Formal letter. | Director with DPO | As required by law or contract. |
| **Media and public** | Holding statement. | Website; social media. | COM, approved by Director | Only if needed. |

***Initial learner notice (subject: Northbridge Skills Institute – service disruption, Monday)***

Dear learner,

Our main site is closed because of flooding and a power failure. We expect it to stay closed for 72 hours and will tell you if that changes. This is not a confirmed cyber incident, and your Microsoft 365 account and email still work.

Today’s 11:00 examination will go ahead. If you booked a centre workstation, report to \[alternate venue address\] by 10:30 with your student ID. If you chose to use your own device, bring it fully charged and sign in with your Northbridge account. Some centre candidates may sit later in the day; we will email your time slot.

Fee confirmation and admissions will continue through temporary arrangements. Please keep your payment receipts and do not pay twice.

We will email updates every few hours. Contact \[support email or phone\] for accessibility needs.

Examinations and Student Services

Incident response takes over decisions when a credible indicator of compromise appears: an unexpected backup administrator logon, failed integrity or hash checks, unexplained changes, missing logs, a ransom note, or payments missing without explanation. The trigger pauses the affected restore step, preserves evidence, isolates the backup repository, rotates shared credentials, and requires IR clearance before restoration resumes. The Data Protection Officer then assesses notification duties ([Nelson et al., 2025\)](https://csrc.nist.gov/pubs/sp/800/61/r3/final).

Safe return needs seven conditions: written facilities clearance (structure, electrics, water ingress, fire safety, drying); stable power and network; a freeze window in which recovery systems stop accepting changes; controlled transfer, which exports new and changed records since the restore point, validates counts and totals, imports them to primary systems and reconciles against temporary registers; sample validation by function owners; a parallel run until reconciliation closes; and final sign-off by the Director after facilities clearance, business validation and IR clearance. Temporary services close only after that sign-off.

# **Task 5: Recovery Schedule and Exercise**

## **5.1 Baseline recovery schedule (modelled)**

Table 13 is the modelled baseline for the current warm site timings, starting at 08:00 with technicians T1 and T2. The controlling path is Recovery network (30) → AUTH01 (30) → Security and backup checks (30) → DB01 (90) → LMS01 (45), totalling 225 minutes, so the assessment service is restored at 11:45 at the earliest. While T1 restores DB01, T2 restores FS01 (09:30 to 10:30). After DB01 finishes at 11:00, the four applications need 150 technician-minutes; shared evenly, each technician works 75 minutes, so all five functions are restored by 12:15. No schedule can finish sooner, because the DB01 path ends at 11:00 and 150 minutes cannot be split below 75 each.

***Table 13: Baseline recovery schedule (modelled)***

| \# | Action | Technician | Start | Finish | Minutes | Prerequisite |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| 1 | Recovery network | T1 | 08:00 | 08:30 | 30 | None |
| 2 | AUTH01 restoration | T1 | 08:30 | 09:00 | 30 | Recovery network |
| 3 | Security and backup checks | T1 | 09:00 | 09:30 | 30 | AUTH01 restoration |
| 4 | **DB01 restoration** | T1 | 09:30 | 11:00 | 90 | Security and backup checks |
| 5 | FS01 restoration | T2 | 09:30 | 10:30 | 60 | AUTH01 restoration; security and backup checks |
| 6 | **LMS01 restoration** | T1 | 11:00 | 11:45 | 45 | DB01 restoration |
| 7 | FIN01 restoration | T2 | 11:00 | 11:30 | 30 | DB01 restoration |
| 8 | HR01 restoration | T2 | 11:30 | 12:15 | 45 | DB01 restoration |
| 9 | REG01 restoration | T1 | 11:45 | 12:15 | 30 | DB01 restoration |

T2 is idle from 08:00 to 09:30 and 10:30 to 11:00; that time is used for alternate-site and continuity set-up. Critical path: actions 1, 2, 3, 4 and 6\.

Table 14 compares elapsed time from 08:00 with the Task 2 targets. Every function meets its modelled RTO and MTD. Restored checkpoints meet the RPO for F1 to F4 (DB01, 1 hour) but not F5 (FS01, 9 hours against 8\) or the shared AUTH01 target (8 hours against 4). These are modelled baseline results, not a live test. Four deadlines need a continuity workaround even when restoration succeeds: the 11:00 examination (LMS01 returns at 11:45 and seats are limited); fee confirmation at 16:00 (FIN01 returns at 11:30 holding 07:00 data, so provider reconciliation is required); admissions at 18:00 (applications since 07:00 must be re-captured); and the payroll bank file at 12:00 on Day 1 (HR01 data and changes must be verified manually).

***Table 14: Elapsed time and checkpoint comparison***

| Function | Restored at | Elapsed | RTO | MTD | RTO / MTD result | Checkpoint age vs RPO | Workaround needed |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| **F1 (LMS01)** | 11:45 | 3 h 45 min | 4 h | 8 h | Met; 15 min margin | 1 h vs 1 h: met | Yes: 11:00 exam; seat limit. |
| **F2 (FIN01)** | 11:30 | 3 h 30 min | 5 h | 8 h | Met | 1 h vs 1 h: met | Yes: provider reconciliation before 16:00. |
| **F3 (REG01)** | 12:15 | 4 h 15 min | 6 h | 10 h | Met | 1 h vs 4 h: met | Yes: re-capture applications since 07:00. |
| **F4 (HR01)** | 12:15 | 4 h 15 min | 8 h | 24 h | Met | 1 h vs 4 h: met | Yes: manual payroll verification. |
| **F5 (FS01)** | 10:30 | 2 h 30 min | 24 h | 48 h | Met | 9 h vs 8 h: breach | Request log until accepted. |

## **5.2 Tabletop exercise (stress scenario)**

The 45-minute tabletop is a stress scenario kept separate from the baseline schedule. I simulate each role in turn: Director, Coordinator, Technical Recovery Lead, Facilities Manager, IR Lead, Examinations Officer, Finance Manager and Communications Lead. Minutes 0 to 10 confirm the baseline plan. Each inject then receives a decision, owner, rationale and effect (Table 15). For inject 3 I assume the 05:00 incremental is the one that fails, so the last contiguous valid point is 04:00, four hours before the disruption.

***Table 15: Tabletop exercise log***

| Minute | Inject | Decision and revised action | Owner | Rationale | Effect on service or recovery |
| :---- | :---- | :---- | :---- | :---- | :---- |
| 10 | Closure extends from 72 hours to five days. | Declare an extended-outage phase; extend the alternate facility booking and warm site use to Day 5; turn temporary procedures into daily routines; build a three-person technical rota; update all stakeholders. | Director | A 120-hour outage exceeds the 72-hour assumptions: manual workarounds degrade, deadlines recur and two technicians cannot cover it. | Baseline restore times unchanged (12:15). Dependence on the alternate site, warm site and staff lengthens; return date moves. |
| 20 | Alternate facility can provide only 15 working workstations. | Give the 15 seats to learners with accessibility adjustments and those with no alternative; run the other 25 centre candidates in two further sittings (15 and 10\) on equivalent forms, supervised between sittings; ask the facility for replacement units. | Examinations Officer | Protects integrity and still provides an acceptable service at 11:00 for 15 centre and 80 own-device learners. | Three sittings; last sitting ends later. Risk that the rescheduling cost applies to delayed learners, which the Director accepts. |
| 30 | DB01 incremental fails its integrity check; unexpected backup administrator logon. | Hold DB01 restore; IR opens an incident; isolate the backup repository; rotate shared credentials; verify B01 and every increment; restore to 04:00 only after IR clearance; use the 17:00 Day −3 full only as a last resort. | IR Lead | Integrity comes before speed; the shared identity means production and backups may both be exposed. | DB01 and LMS01 delayed by an assumed 30 to 60 min (LMS01 about 12:15 to 12:45). Data age 4 h breaches F1 and F2 RPO and meets F3 and F4. |
| 40 | Payment provider reports successful payments absent from restored finance records. | Treat the provider report as authoritative; export provider transactions from 04:00 to now; post them by dual control after acceptance; send provisional fee confirmations; ask IR whether records were deleted. | Finance Manager | Gaps are expected from the 4-hour data loss, but unexplained gaps could signal tampering; learners must not be charged twice. | F2 is restored but not resumed until reconciled; the 16:00 confirmation relies on provider data; duplicate-payment risk managed. |

The tabletop shows that the plan's weakest links are the shared administrator identity, the thin data-age margin for F1 and F2, and the seat limit at the alternate venue. Each inject changes a decision, not the baseline schedule, and the weaknesses appear as corrective actions CA1, CA3, CA5 and CA8.

## **5.3 Corrective actions**

Table 16 lists corrective actions from the baseline and tabletop. Target dates assume plan approval in early November 2026\.

***Table 16: Corrective action register***

| ID | Action | Pri. | Owner | Target date | Measurable completion evidence |
| :---- | :---- | :---- | :---- | :---- | :---- |
| CA1 | Separate the backup administrator identity from production; enforce multi-factor authentication, two-person deletion approval and logon alerts. | P1 | IR Lead | 13 Nov 2026 | Access review shows no shared admin account; test shows production admin cannot delete backups; alert test logged. |
| CA2 | Obtain the offsite provider’s access-independence documentation and test restore with independent credentials. | P1 | Technical Recovery Lead | 30 Nov 2026 | Signed provider attestation and a successful independent-credential restore record. |
| CA3 | Implement hourly DB01 incrementals, 4-hourly AUTH01, FS01 at 07:00 and 15:00, and the immutable copy. | P1 | Technical Recovery Lead | 18 Dec 2026 | Backup reports show 14 consecutive days with every checkpoint inside its RPO. |
| CA4 | Run a full DB01 chain restore in isolation with timings; automate weekly hash verification. | P1 | Technical Recovery Lead | 29 Jan 2027 | Signed test record: chain verified, LMS01 available within 4 h. |
| CA5 | Pilot the temporary Microsoft 365 assessment with the 25-seat and 15-seat plans. | P2 | Examinations Officer | 28 Feb 2027 | Pilot report: all pilot candidates authenticated; submissions logged; invigilation checklist complete. |
| CA6 | Create a daily payment provider export and reconciliation procedure. | P2 | Finance Manager | 15 Jan 2027 | Drill reconciles provider report to ledger with NGN 0 unexplained difference within 2 hours. |
| CA7 | Cross-train a third technician and build a five-day (120-hour) rota. | P2 | Technical Recovery Lead | 31 Mar 2027 | Training records and a rota covering 120 hours. |
| CA8 | Contract a minimum of 25 working workstations at the alternate facility with a 4-hour confirmation service level. | P2 | Facilities Manager | 28 Feb 2027 | Signed service level agreement. |

## 

# **Task 6: Governance and Performance Measures**

## **6.1 Ownership, testing and maintenance**

The BC/DR Coordinator owns the plan and the Institute Director approves it; the governing board receives an annual summary. Each approved version is recorded in a document register and distributed through a restricted Microsoft 365 library and offline copies held by the Director, deputy and Technical Recovery Lead. Testing is risk-based (Table 17), with extra review after any incident, failed test, system, supplier or premises change, or flood alert. Role holders are trained within 30 days of appointment and refreshed annually.

***Table 17: Testing and maintenance calendar***

| Activity | Schedule | Extra review triggers | Owner |
| :---- | :---- | :---- | :---- |
| **Backup integrity verification** | Weekly automated; monthly report. | Any failed job or restore error. | Technical Recovery Lead |
| **Isolated restore test (DB01 chain, AUTH01, FS01)** | Quarterly. | Backup design change; failed integrity check. | Technical Recovery Lead |
| **Communications and call-tree test** | Quarterly. | Role-holder change. | BC/DR Coordinator |
| **Tabletop exercise** | Twice yearly; one before the rainy season. | Major incident elsewhere; plan change. | BC/DR Coordinator |
| **Warm-site recovery exercise** | Annually, before the rainy season. | Supplier or site change; failed tabletop. | Director (sponsor); Technical Recovery Lead |
| **Plan review and version control** | Annually; register records version, date, author, approver and change summary. | Any activation, test failure, or major system, supplier, premises or organisational change. | BC/DR Coordinator |
| **Training** | New role holders within 30 days; annual refresher; attendance recorded. | Plan revision. | BC/DR Coordinator with HR |

## **6.2 Framework mapping**

Using slides 4 and 9, Tables 18 and 19 map outputs to the seven NIST SP 800-34 planning steps and to ISO 22301 clauses 4 to 10\.

***Table 18: NIST SP 800-34 mapping***

| NIST step | Output in this report | Task |
| :---- | :---- | :---- |
| **1 Contingency planning policy statement** | Scope, activation thresholds, ownership, approval and distribution. | 4, 6 |
| **2 Business impact analysis** | BIA tables, impact calculations, objective matrix. | 1, 2 |
| **3 Preventive controls** | Backup design: 3-2-1, immutable copy, separate administrator, encryption; flood siting. | 2, 6 |
| **4 Contingency strategies** | Option comparison, budget and Warm recommendation. | 3 |
| **5 Contingency plan development** | Plan, RACI, temporary procedures, runbook, communication matrix, notice. | 4 |
| **6 Testing, training and exercises** | Baseline schedule, tabletop, corrective actions, testing calendar. | 5, 6 |
| **7 Plan maintenance** | Version control, review triggers, KPIs, corrective-action closure. | 6 |

***Table 19: ISO 22301 mapping***

| ISO 22301 clause | Output in this report | Task |
| :---- | :---- | :---- |
| **4 Context** | Stakeholder matrix; flood and climate considerations; scope. | 4, 6 |
| **5 Leadership** | Director as decision maker; plan ownership and approval. | 4, 6 |
| **6 Planning** | Dependency risks; RTO, RPO and MTD objectives; KPI targets. | 1, 2, 6 |
| **7 Support** | Minimum staff, equipment and suppliers; training; communication; version control. | 4, 6 |
| **8 Operation** | BIA, strategy, backup design, runbook, temporary procedures, exercises. | 1 to 5 |
| **9 Performance** | KPIs, restoration tests, dashboard, maturity assessment. | 5, 6 |
| **10 Improvement** | Corrective action register and post-exercise review. | 5 |

## **6.3 Flood and climate consideration**

ISO 22301:2019/Amd 1:2024 adds climate action changes, so the context analysis should ask whether climate change is a relevant issue. Flooding is a direct example: the main site and its local systems sit inside the affected footprint. The warm site, alternate facility and offsite backups should therefore sit in a different flood zone and power grid, with seasonal readiness checks, flood-alert monitoring, equipment kept above flood level and a review of generator fuel and site access.

## **6.4 KPIs and maturity**

Table 20 defines six KPIs with baselines from the modelled results and current evidence. Using the slide 13 maturity model (ICDFA, n.d., slide 13), Northbridge is at Level 2, Developing: backups and warm-site timings exist, but restoration is untested, the backup administrator identity is shared, and objectives were not previously tied to a BIA. A realistic 12-month target is Level 3, Defined, shown by documented processes, regular testing, clear governance and consistent recovery across two successive quarterly tests (Table 21). Level 4 needs a longer measured history, so it is unrealistic within 12 months. KPIs are reported monthly to the Director and quarterly to the board, and any red status needs a dated recovery action.

***Table 20: KPI dashboard***

| KPI | Formula or method | Data source | Target | Frequency | Owner | Baseline |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| **Recovery time performance** | Functions meeting RTO ÷ functions tested × 100 | Exercise and incident timestamps | 100% for F1 to F4; at least 90% overall | Each test; quarterly report | Technical Recovery Lead | 100% (5 of 5), modelled only; no live test |
| **RPO attainment** | Functions with checkpoint age ≤ RPO ÷ functions × 100 | Backup catalogue timestamps | 100% | Monthly | Technical Recovery Lead | 80% (4 of 5); F5 and AUTH01 breach |
| **Restoration-test coverage** | Backup sets restore-tested in last 90 days ÷ total sets × 100 | Restore test records | 100% | Quarterly | Technical Recovery Lead | No test evidenced |
| **Corrective-action closure** | Actions closed by target date ÷ actions due × 100 | Corrective action register | At least 90% | Monthly | BC/DR Coordinator | 0 of 8 closed (new) |
| **Training completion** | Role holders trained in last 12 months ÷ role holders × 100 | Training records | 100% role holders; 90% staff awareness | Quarterly | BC/DR Coordinator with HR | Not evidenced |
| **Backup verification success** | Verified backup jobs ÷ scheduled jobs × 100 | Backup logs | At least 99% | Weekly | Technical Recovery Lead | Not measured |

***Table 21: Maturity and 12-month target***

| Area | Current evidence (Level 2, Developing) | Target by October 2027 (Level 3, Defined) | Milestones |
| :---- | :---- | :---- | :---- |
| **Plans and objectives** | Recovery timings exist; objectives now defined in this report. | Approved, documented plan tied to the BIA. | Director approves plan by December 2026\. |
| **Testing** | No restore test evidenced. | Quarterly restore tests, two tabletops, one warm-site exercise. | First chain restore January 2027; first tabletop February 2027\. |
| **Governance** | Ownership informal. | Named owner and approver; monthly KPI reporting. | KPI pack from January 2027\. |
| **Backup safeguards** | Shared administrator identity; provider independence undocumented. | Separate identities, immutable copy, verified independence. | CA1 to CA3 closed by December 2026\. |
| **Overall** | **Level 2** | **Level 3** | Reassess October 2027\. |

# **References**

* ICDFA (n.d.) *Business Continuity and Disaster Recovery*. GRC205 Incident Management and Business Continuity. Teaching deck, slides 4, 9 and 13\. International Cybersecurity and Digital Forensics Academy, E-Campus.  
* ISO (2019) *ISO 22301:2019 Security and resilience — Business continuity management systems — Requirements*. Geneva: International Organization for Standardization.  
  [https\://www\.iso.org/standard/75106.html](https://www.iso.org/standard/75106.html).

* ISO (2024) *ISO 22301:2019/Amd 1:2024 Security and resilience — Business continuity management systems — Requirements — Amendment 1: Climate action changes*. Geneva: International Organization for Standardization.  
  [https\://www\.iso.org/standard/88412.html](https://www.iso.org/standard/88412.html).

* Nelson, A., Rekhi, S., Scarfone, K. and Souppaya, M. (2025) *NIST SP 800-61 Rev. 3: Incident Response Recommendations and Considerations for Cybersecurity Risk Management: A CSF 2.0 Community Profile*. Gaithersburg, MD: National Institute of Standards and Technology.  
  [https\://csrc.nist.gov/pubs/sp/800/61/r3/final](https://csrc.nist.gov/pubs/sp/800/61/r3/final).

* NIST (2010) *SP 800-34 Rev. 1: Contingency Planning Guide for Federal Information Systems*. Gaithersburg, MD: National Institute of Standards and Technology.  
  [https\://csrc.nist.gov/pubs/sp/800/34/r1/upd1/final](https://csrc.nist.gov/pubs/sp/800/34/r1/upd1/final).
