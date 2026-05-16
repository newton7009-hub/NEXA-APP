import React, { useState, useEffect, useRef, useCallback } from 'react';
import {
  View,
  Text,
  StyleSheet,
  TextInput,
  TouchableOpacity,
  ScrollView,
  Alert,
  ActivityIndicator,
  Modal,
  Animated,
  Vibration,
  Platform,
  KeyboardAvoidingView,
} from 'react-native';
import { Ionicons } from '@expo/vector-icons';

/* ─── COLOR PALETTE ───────────────────────────────────────────────────────────── */
const GOLD = '#c9a84c';
const ACCENT = '#4cd1ff';
const BG = '#0f1923';
const CARD = '#1a2738';
const CARD2 = '#243447';
const WHITE = '#f0f4f8';
const MUTED = '#8a9bb0';
const DANGER = '#f87171';
const GREEN = '#22c55e';
const AMBER = '#f59e0b';
const PURPLE = '#a78bfa';

/* ─── ROLE DEFINITIONS ────────────────────────────────────────────────────────── */
const ROLES = {
  admin: { label: 'Administrator', icon: 'shield-outline', color: GOLD },
  chef: { label: 'Chef', icon: 'restaurant-outline', color: AMBER },
  staff: { label: 'Staff', icon: 'people-outline', color: ACCENT },
  analytics: { label: 'Analytics', icon: 'bar-chart-outline', color: PURPLE },
  manager: { label: 'Manager', icon: 'briefcase-outline', color: GREEN },
  security: { label: 'Security', icon: 'lock-closed-outline', color: DANGER },
};

/* ─── STAFF CREDENTIALS (tight security — all roles have ID + name) ───────────── */
const STAFF_CREDENTIALS = [
  {
    id: 'ADM-001',
    name: 'Sarah Johnson',
    role: 'admin',
    pin: '4821',
    email: 'admin@nexahotel.com',
    dept: 'Management',
    shift: 'All Day',
    access: ['admin', 'chef', 'staff', 'analytics', 'manager', 'security'],
  },
  {
    id: 'MGR-001',
    name: 'David Ochieng',
    role: 'manager',
    pin: '6193',
    email: 'manager@nexahotel.com',
    dept: 'Operations',
    shift: '8AM–6PM',
    access: ['manager', 'staff', 'analytics'],
  },
  {
    id: 'CHF-001',
    name: 'Marco Rossi',
    role: 'chef',
    pin: '7364',
    email: 'chef@nexahotel.com',
    dept: 'Kitchen',
    shift: '7AM–4PM',
    access: ['chef'],
  },
  {
    id: 'CHF-002',
    name: 'Aisha Kimani',
    role: 'chef',
    pin: '2193',
    email: 'chef2@nexahotel.com',
    dept: 'Kitchen',
    shift: '3PM–12AM',
    access: ['chef'],
  },
  {
    id: 'STF-001',
    name: 'Carlos Mendez',
    role: 'staff',
    pin: '5507',
    email: 'staff@nexahotel.com',
    dept: 'Front Office',
    shift: 'Morning',
    access: ['staff'],
  },
  {
    id: 'STF-002',
    name: 'Diana Omondi',
    role: 'staff',
    pin: '8830',
    email: 'staff2@nexahotel.com',
    dept: 'Housekeeping',
    shift: 'Afternoon',
    access: ['staff'],
  },
  {
    id: 'ANA-001',
    name: 'James Waweru',
    role: 'analytics',
    pin: '3312',
    email: 'analytics@nexahotel.com',
    dept: 'Business Intel',
    shift: 'Flexible',
    access: ['analytics'],
  },
  {
    id: 'SEC-001',
    name: 'Felix Otieno',
    role: 'security',
    pin: '9047',
    email: 'security@nexahotel.com',
    dept: 'Security',
    shift: 'Night',
    access: ['security', 'staff'],
  },
];

const MAX_ATTEMPTS = 3;
const LOCKOUT_SECONDS = 30;
const SESSION_TIMEOUT = 30 * 60; // 30 minutes in seconds

/* ─── AUDIT LOG (in-memory for demo) ─────────────────────────────────────────── */
const auditLog = [];
const logEvent = (type, detail) => {
  auditLog.unshift({
    type,
    detail,
    time: new Date().toLocaleTimeString(),
    date: new Date().toLocaleDateString(),
  });
  if (auditLog.length > 100) auditLog.pop();
};

/* ─── HOTEL BACKGROUND ────────────────────────────────────────────────────────── */
function HotelBg() {
  return (
    <View
      style={{
        position: 'absolute',
        top: 0,
        left: 0,
        right: 0,
        bottom: 0,
        overflow: 'hidden',
      }}>
      <View
        style={{
          position: 'absolute',
          top: -120,
          alignSelf: 'center',
          width: 280,
          height: 280,
          borderRadius: 140,
          borderWidth: 2,
          borderColor: '#c9a84c18',
        }}
      />
      <View
        style={{
          position: 'absolute',
          top: -80,
          alignSelf: 'center',
          width: 200,
          height: 200,
          borderRadius: 100,
          borderWidth: 1,
          borderColor: '#c9a84c10',
        }}
      />
      <View
        style={{
          position: 'absolute',
          top: 30,
          left: -30,
          width: 120,
          height: 120,
          borderRadius: 60,
          borderWidth: 1,
          borderColor: '#c9a84c14',
        }}
      />
      <View
        style={{
          position: 'absolute',
          top: 20,
          right: -40,
          width: 140,
          height: 140,
          borderRadius: 70,
          borderWidth: 1,
          borderColor: '#c9a84c10',
        }}
      />
      <View
        style={{
          position: 'absolute',
          top: 180,
          left: 30,
          right: 30,
          height: 1,
          backgroundColor: '#c9a84c12',
        }}
      />
      <View
        style={{
          position: 'absolute',
          bottom: -100,
          alignSelf: 'center',
          width: 320,
          height: 200,
          borderRadius: 160,
          borderWidth: 2,
          borderColor: '#c9a84c14',
        }}
      />
      {[40, 80, 120, 160, 200, 240, 280].map((x, i) => (
        <View
          key={i}
          style={{
            position: 'absolute',
            top: 178,
            left: x,
            width: 4,
            height: 4,
            borderRadius: 2,
            backgroundColor: '#c9a84c30',
          }}
        />
      ))}
    </View>
  );
}

/* ─── SUPPORT MODAL ───────────────────────────────────────────────────────────── */
function SupportModal({ visible, onClose, currentUser }) {
  const [tab, setTab] = useState('faq');
  const [msg, setMsg] = useState('');
  const [sent, setSent] = useState(false);
  const [ticket, setTicket] = useState('');

  const faqs = [
    {
      q: 'How do I reset my PIN?',
      a: 'Contact your hotel admin (ADM-001) to reset your staff PIN. Security policy requires in-person verification.',
    },
    {
      q: 'How do I add a booking?',
      a: 'Go to your Dashboard, find Recent Bookings and tap the + Add button. Only admin and manager roles can add bookings.',
    },
    {
      q: 'Can two staff share a login?',
      a: 'No. Each staff member has a unique ID and PIN for full audit trail. Sharing credentials is a policy violation.',
    },
    {
      q: 'What if I get locked out?',
      a: 'Wait 30 seconds after 3 failed attempts, then retry. For persistent issues, contact your admin immediately.',
    },
    {
      q: 'How do guests book rooms?',
      a: 'Select Guest from the login screen (no credentials needed) and use the Guest Portal.',
    },
    {
      q: 'How do I export analytics?',
      a: 'Go to Analytics Dashboard and tap Export Report. Only analytics and admin roles have export access.',
    },
    {
      q: 'Is payment data stored?',
      a: 'No. Payment data is never stored on device. All transactions are processed by PCI DSS-compliant providers.',
    },
    {
      q: 'What is session timeout?',
      a: 'Sessions auto-expire after 30 minutes of inactivity for security. You will be prompted to log in again.',
    },
    {
      q: 'Who can access audit logs?',
      a: 'Only Admin and Manager roles can view the full audit log under Security settings.',
    },
  ];

  const sendMsg = () => {
    if (!msg.trim()) {
      Alert.alert('Please type a message.');
      return;
    }
    const ref = 'TKT-' + Date.now().toString().slice(-6);
    setTicket(ref);
    setSent(true);
    logEvent('SUPPORT', 'Ticket raised: ' + ref);
    setTimeout(() => {
      setSent(false);
      setMsg('');
      setTicket('');
    }, 3500);
  };

  return (
    <Modal visible={visible} animationType="slide" transparent>
      <View
        style={{
          flex: 1,
          backgroundColor: '#000000aa',
          justifyContent: 'flex-end',
        }}>
        <View
          style={{
            backgroundColor: CARD,
            borderTopLeftRadius: 20,
            borderTopRightRadius: 20,
            maxHeight: '85%',
            padding: 20,
          }}>
          {/* Header */}
          <View
            style={{
              flexDirection: 'row',
              justifyContent: 'space-between',
              alignItems: 'center',
              marginBottom: 16,
            }}>
            <View style={{ flexDirection: 'row', alignItems: 'center' }}>
              <Ionicons name="headset-outline" size={22} color={GOLD} />
              <Text
                style={{
                  color: WHITE,
                  fontWeight: 'bold',
                  fontSize: 18,
                  marginLeft: 8,
                }}>
                Support Centre
              </Text>
            </View>
            <TouchableOpacity onPress={onClose}>
              <Ionicons name="close-circle-outline" size={26} color={MUTED} />
            </TouchableOpacity>
          </View>

          {/* Tabs */}
          <View style={{ flexDirection: 'row', marginBottom: 14 }}>
            {['faq', 'contact', 'status', 'ticket'].map((t) => (
              <TouchableOpacity
                key={t}
                onPress={() => setTab(t)}
                style={[
                  styles.chip,
                  tab === t && styles.chipActive,
                  { marginRight: 6, paddingHorizontal: 10 },
                ]}>
                <Text
                  style={[
                    styles.chipText,
                    tab === t && { color: '#1a1200' },
                    { fontSize: 11 },
                  ]}>
                  {t === 'faq'
                    ? 'FAQs'
                    : t === 'contact'
                    ? 'Contact'
                    : t === 'status'
                    ? 'System'
                    : 'My Ticket'}
                </Text>
              </TouchableOpacity>
            ))}
          </View>

          <ScrollView showsVerticalScrollIndicator={false}>
            {/* FAQs */}
            {tab === 'faq' &&
              faqs.map((f, i) => (
                <View
                  key={i}
                  style={{
                    backgroundColor: CARD2,
                    borderRadius: 10,
                    padding: 12,
                    marginBottom: 8,
                  }}>
                  <Text
                    style={{
                      color: GOLD,
                      fontWeight: 'bold',
                      fontSize: 12,
                      marginBottom: 4,
                    }}>
                    {'Q: ' + f.q}
                  </Text>
                  <Text style={{ color: MUTED, fontSize: 12 }}>
                    {'A: ' + f.a}
                  </Text>
                </View>
              ))}

            {/* Contact */}
            {tab === 'contact' && (
              <View>
                {[
                  {
                    icon: 'call-outline',
                    label: 'Emergency Hotline',
                    val: '+254 795608151',
                    highlight: true,
                  },
                  {
                    icon: 'call-outline',
                    label: 'Support Phone',
                    val: '+254 703684899',
                  },
                  {
                    icon: 'mail-outline',
                    label: 'Email',
                    val: 'support@nexahotel.com',
                  },
                  {
                    icon: 'logo-whatsapp',
                    label: 'WhatsApp',
                    val: '+254 140393638',
                  },
                  {
                    icon: 'globe-outline',
                    label: 'Help Portal',
                    val: 'help.nexahotel.com',
                  },
                  {
                    icon: 'time-outline',
                    label: 'Hours',
                    val: '24/7 Available',
                  },
                ].map((c) => (
                  <View
                    key={c.label}
                    style={{
                      flexDirection: 'row',
                      alignItems: 'center',
                      backgroundColor: c.highlight ? DANGER + '22' : CARD2,
                      borderRadius: 10,
                      padding: 12,
                      marginBottom: 8,
                      borderWidth: c.highlight ? 1 : 0,
                      borderColor: DANGER + '44',
                    }}>
                    <Ionicons
                      name={c.icon}
                      size={20}
                      color={c.highlight ? DANGER : GOLD}
                    />
                    <View style={{ marginLeft: 12 }}>
                      <Text style={{ color: MUTED, fontSize: 11 }}>
                        {c.label}
                      </Text>
                      <Text
                        style={{
                          color: c.highlight ? DANGER : WHITE,
                          fontWeight: 'bold',
                        }}>
                        {c.val}
                      </Text>
                    </View>
                  </View>
                ))}
                <Text
                  style={{
                    color: MUTED,
                    fontSize: 12,
                    marginTop: 8,
                    marginBottom: 6,
                  }}>
                  Send a message
                </Text>
                <View style={[styles.inputWrap, { width: '100%' }]}>
                  <TextInput
                    placeholder="Describe your issue…"
                    placeholderTextColor={MUTED}
                    style={[
                      styles.inputField,
                      { height: 70, textAlignVertical: 'top' },
                    ]}
                    multiline
                    value={msg}
                    onChangeText={setMsg}
                  />
                </View>
                <TouchableOpacity
                  style={[styles.mainBtn, { width: '100%', marginTop: 8 }]}
                  onPress={sendMsg}>
                  {sent ? (
                    <Text style={styles.btnText}>{'Sent! Ref: ' + ticket}</Text>
                  ) : (
                    <Text style={styles.btnText}>Send Message</Text>
                  )}
                </TouchableOpacity>
              </View>
            )}

            {/* System Status */}
            {tab === 'status' && (
              <View>
                <Text style={{ color: MUTED, fontSize: 12, marginBottom: 10 }}>
                  Live system component status
                </Text>
                {[
                  { name: 'Booking Engine', ok: true },
                  { name: 'Payment Gateway', ok: true },
                  { name: 'Kitchen Display', ok: true },
                  { name: 'Analytics Engine', ok: true },
                  { name: 'SMS Alerts', ok: false },
                  { name: 'Email Service', ok: true },
                  { name: 'Security Audit', ok: true },
                  { name: 'Backup Systems', ok: true },
                ].map((s) => (
                  <View
                    key={s.name}
                    style={{
                      flexDirection: 'row',
                      justifyContent: 'space-between',
                      alignItems: 'center',
                      backgroundColor: CARD2,
                      borderRadius: 10,
                      padding: 12,
                      marginBottom: 8,
                    }}>
                    <Text style={{ color: WHITE, fontSize: 13 }}>{s.name}</Text>
                    <View
                      style={{ flexDirection: 'row', alignItems: 'center' }}>
                      <View
                        style={{
                          width: 8,
                          height: 8,
                          borderRadius: 4,
                          backgroundColor: s.ok ? GREEN : DANGER,
                          marginRight: 6,
                        }}
                      />
                      <Text
                        style={{ color: s.ok ? GREEN : DANGER, fontSize: 12 }}>
                        {s.ok ? 'Operational' : 'Degraded'}
                      </Text>
                    </View>
                  </View>
                ))}
              </View>
            )}

            {/* My Ticket */}
            {tab === 'ticket' && (
              <View>
                <Text style={{ color: MUTED, fontSize: 12, marginBottom: 12 }}>
                  Raise a formal support ticket
                </Text>
                {currentUser && (
                  <View
                    style={{
                      backgroundColor: CARD2,
                      borderRadius: 10,
                      padding: 12,
                      marginBottom: 12,
                    }}>
                    <Text style={{ color: MUTED, fontSize: 11 }}>
                      Submitting as
                    </Text>
                    <Text style={{ color: WHITE, fontWeight: 'bold' }}>
                      {currentUser.name + ' (' + currentUser.id + ')'}
                    </Text>
                  </View>
                )}
                {[
                  { placeholder: 'Issue title', multiline: false },
                  {
                    placeholder: 'Full description of the issue…',
                    multiline: true,
                  },
                ].map((f, i) => (
                  <View
                    key={i}
                    style={[
                      styles.inputWrap,
                      { width: '100%', marginBottom: 8 },
                    ]}>
                    <TextInput
                      placeholder={f.placeholder}
                      placeholderTextColor={MUTED}
                      style={[
                        styles.inputField,
                        f.multiline && { height: 70, textAlignVertical: 'top' },
                      ]}
                      multiline={f.multiline}
                    />
                  </View>
                ))}
                <TouchableOpacity
                  style={[styles.mainBtn, { width: '100%', marginTop: 4 }]}
                  onPress={() => {
                    const ref = 'TKT-' + Date.now().toString().slice(-6);
                    Alert.alert(
                      'Ticket Submitted',
                      'Your ticket ' +
                        ref +
                        ' has been raised.\nExpected response: within 2 hours.'
                    );
                    logEvent('SUPPORT_TICKET', ref);
                  }}>
                  <Ionicons
                    name="ticket-outline"
                    size={16}
                    color="#1a1200"
                    style={{ marginRight: 6 }}
                  />
                  <Text style={styles.btnText}>Submit Ticket</Text>
                </TouchableOpacity>
              </View>
            )}
          </ScrollView>
        </View>
      </View>
    </Modal>
  );
}

/* ─── HAMBURGER MENU DRAWER ───────────────────────────────────────────────────── */
function MenuDrawer({
  visible,
  onClose,
  screen,
  setScreenFn,
  handleLogout,
  currentUser,
}) {
  const slideAnim = useRef(new Animated.Value(-300)).current;

  useEffect(() => {
    Animated.spring(slideAnim, {
      toValue: visible ? 0 : -300,
      useNativeDriver: true,
      tension: 80,
      friction: 12,
    }).start();
  }, [visible]);

  const allNavItems = [
    {
      icon: 'shield-outline',
      label: 'Admin',
      target: 'admin',
      roles: ['admin'],
    },
    {
      icon: 'briefcase-outline',
      label: 'Manager',
      target: 'manager',
      roles: ['admin', 'manager'],
    },
    {
      icon: 'restaurant-outline',
      label: 'Chef',
      target: 'chef',
      roles: ['admin', 'chef'],
    },
    {
      icon: 'people-outline',
      label: 'Staff',
      target: 'staff',
      roles: ['admin', 'manager', 'staff', 'security'],
    },
    {
      icon: 'bar-chart-outline',
      label: 'Analytics',
      target: 'analytics',
      roles: ['admin', 'manager', 'analytics'],
    },
    {
      icon: 'lock-closed-outline',
      label: 'Security',
      target: 'security',
      roles: ['admin', 'security'],
    },
    {
      icon: 'person-outline',
      label: 'Guest Portal',
      target: 'guest',
      roles: ['admin', 'manager', 'staff'],
    },
  ];

  const items = currentUser
    ? allNavItems.filter((i) => i.roles.includes(currentUser.role))
    : [];

  if (!visible) return null;

  return (
    <View
      style={{
        position: 'absolute',
        top: 0,
        left: 0,
        right: 0,
        bottom: 0,
        zIndex: 500,
        flexDirection: 'row',
      }}>
      <Animated.View
        style={{
          width: '75%',
          backgroundColor: CARD,
          height: '100%',
          padding: 24,
          paddingTop: 50,
          transform: [{ translateX: slideAnim }],
        }}>
        {/* Hotel logo in drawer */}
        <View
          style={{
            marginBottom: 20,
            paddingBottom: 16,
            borderBottomWidth: 1,
            borderBottomColor: '#ffffff10',
            alignItems: 'center',
          }}>
          <Ionicons name="diamond-outline" size={22} color={GOLD} />
          <Text
            style={{
              color: GOLD,
              fontWeight: 'bold',
              fontSize: 18,
              letterSpacing: 4,
              marginTop: 4,
            }}>
            NEXA
          </Text>
        </View>

        {/* Logged-in user info */}
        {currentUser && (
          <View
            style={{
              marginBottom: 20,
              paddingBottom: 16,
              borderBottomWidth: 1,
              borderBottomColor: '#ffffff10',
            }}>
            <View
              style={{
                flexDirection: 'row',
                alignItems: 'center',
                marginBottom: 8,
              }}>
              <View
                style={{
                  backgroundColor: GOLD + '22',
                  borderRadius: 22,
                  width: 44,
                  height: 44,
                  justifyContent: 'center',
                  alignItems: 'center',
                  marginRight: 10,
                }}>
                <Ionicons
                  name={ROLES[currentUser.role]?.icon || 'person-outline'}
                  size={22}
                  color={GOLD}
                />
              </View>
              <View style={{ flex: 1 }}>
                <Text
                  style={{ color: WHITE, fontWeight: 'bold', fontSize: 14 }}>
                  {currentUser.name}
                </Text>
                <Text style={{ color: GOLD, fontSize: 11 }}>
                  {currentUser.id}
                </Text>
              </View>
            </View>
            <View style={{ flexDirection: 'row', flexWrap: 'wrap', gap: 6 }}>
              <View
                style={{
                  backgroundColor: ROLES[currentUser.role]?.color + '22',
                  borderRadius: 10,
                  paddingHorizontal: 8,
                  paddingVertical: 3,
                }}>
                <Text
                  style={{
                    color: ROLES[currentUser.role]?.color,
                    fontSize: 10,
                    fontWeight: 'bold',
                  }}>
                  {ROLES[currentUser.role]?.label?.toUpperCase()}
                </Text>
              </View>
              <View
                style={{
                  backgroundColor: CARD2,
                  borderRadius: 10,
                  paddingHorizontal: 8,
                  paddingVertical: 3,
                }}>
                <Text style={{ color: MUTED, fontSize: 10 }}>
                  {currentUser.shift}
                </Text>
              </View>
              <View
                style={{
                  backgroundColor: CARD2,
                  borderRadius: 10,
                  paddingHorizontal: 8,
                  paddingVertical: 3,
                }}>
                <Text style={{ color: MUTED, fontSize: 10 }}>
                  {currentUser.dept}
                </Text>
              </View>
            </View>
          </View>
        )}

        <Text
          style={{
            color: MUTED,
            fontSize: 10,
            letterSpacing: 2,
            marginBottom: 8,
          }}>
          NAVIGATION
        </Text>
        <ScrollView showsVerticalScrollIndicator={false} style={{ flex: 1 }}>
          {items.map((item) => (
            <TouchableOpacity
              key={item.target}
              onPress={() => {
                setScreenFn(item.target);
                onClose();
              }}
              style={{
                flexDirection: 'row',
                alignItems: 'center',
                paddingVertical: 13,
                borderBottomWidth: 1,
                borderBottomColor: '#ffffff08',
              }}>
              <Ionicons
                name={item.icon}
                size={20}
                color={screen === item.target ? GOLD : MUTED}
              />
              <Text
                style={{
                  color: screen === item.target ? GOLD : WHITE,
                  marginLeft: 14,
                  fontSize: 14,
                  fontWeight: screen === item.target ? 'bold' : 'normal',
                }}>
                {item.label}
              </Text>
              {screen === item.target && (
                <View
                  style={{
                    marginLeft: 'auto',
                    width: 4,
                    height: 16,
                    backgroundColor: GOLD,
                    borderRadius: 2,
                  }}
                />
              )}
            </TouchableOpacity>
          ))}
        </ScrollView>

        {/* Bottom actions */}
        <View
          style={{
            paddingTop: 16,
            borderTopWidth: 1,
            borderTopColor: '#ffffff10',
          }}>
          <TouchableOpacity
            onPress={() => {
              onClose();
              handleLogout();
            }}
            style={{
              flexDirection: 'row',
              alignItems: 'center',
              paddingVertical: 12,
            }}>
            <Ionicons name="log-out-outline" size={20} color={DANGER} />
            <Text
              style={{
                color: DANGER,
                marginLeft: 14,
                fontSize: 14,
                fontWeight: 'bold',
              }}>
              Logout
            </Text>
          </TouchableOpacity>
        </View>
      </Animated.View>

      {/* Tap outside to close */}
      <TouchableOpacity
        style={{ flex: 1, backgroundColor: '#00000060' }}
        onPress={onClose}
      />
    </View>
  );
}

/* ─── TOP BAR ─────────────────────────────────────────────────────────────────── */
function TopBar({ title, onMenu, onSupport, notifs, onNotif, currentUser }) {
  return (
    <View style={styles.topBar}>
      <TouchableOpacity onPress={onMenu} style={styles.topBarBtn}>
        <Ionicons name="menu-outline" size={26} color={WHITE} />
      </TouchableOpacity>
      <View style={{ flex: 1, alignItems: 'center' }}>
        <Text style={styles.topBarTitle}>{title}</Text>
        {currentUser && (
          <Text style={{ color: GOLD, fontSize: 10, marginTop: -2 }}>
            {currentUser.id + ' • ' + ROLES[currentUser.role]?.label}
          </Text>
        )}
      </View>
      <View style={{ flexDirection: 'row', alignItems: 'center' }}>
        {onNotif && (
          <TouchableOpacity
            onPress={onNotif}
            style={[styles.topBarBtn, { marginRight: 2 }]}>
            <Ionicons name="notifications-outline" size={22} color={WHITE} />
            {notifs > 0 && (
              <View style={styles.badge}>
                <Text style={styles.badgeText}>{notifs}</Text>
              </View>
            )}
          </TouchableOpacity>
        )}
        <TouchableOpacity onPress={onSupport} style={styles.topBarBtn}>
          <Ionicons name="headset-outline" size={22} color={GOLD} />
        </TouchableOpacity>
      </View>
    </View>
  );
}

/* ─── SESSION TIMEOUT BANNER ──────────────────────────────────────────────────── */
function SessionBanner({ timeLeft, onExtend }) {
  if (timeLeft > 120) return null;
  return (
    <View
      style={{
        backgroundColor: AMBER + '22',
        padding: 10,
        flexDirection: 'row',
        alignItems: 'center',
        justifyContent: 'space-between',
        borderWidth: 1,
        borderColor: AMBER + '44',
      }}>
      <View style={{ flexDirection: 'row', alignItems: 'center' }}>
        <Ionicons name="time-outline" size={16} color={AMBER} />
        <Text style={{ color: AMBER, fontSize: 12, marginLeft: 6 }}>
          Session expires in {timeLeft}s
        </Text>
      </View>
      <TouchableOpacity
        onPress={onExtend}
        style={{
          backgroundColor: AMBER,
          borderRadius: 8,
          paddingHorizontal: 10,
          paddingVertical: 4,
        }}>
        <Text style={{ color: '#1a1200', fontWeight: 'bold', fontSize: 11 }}>
          Extend
        </Text>
      </TouchableOpacity>
    </View>
  );
}

/* ─── APP ROOT ────────────────────────────────────────────────────────────────── */
export default function App() {
  const [screen, setScreen] = useState('login');
  const [loginKey, setLoginKey] = useState(0);
  const [currentUser, setCurrentUser] = useState(null);
  const [drawerOpen, setDrawerOpen] = useState(false);
  const [supportOpen, setSupportOpen] = useState(false);
  const [sessionTime, setSessionTime] = useState(SESSION_TIMEOUT);
  const sessionRef = useRef(null);

  /* Session countdown */
  useEffect(() => {
    if (currentUser && screen !== 'login') {
      setSessionTime(SESSION_TIMEOUT);
      sessionRef.current = setInterval(() => {
        setSessionTime((t) => {
          if (t <= 1) {
            handleLogout('timeout');
            return 0;
          }
          return t - 1;
        });
      }, 1000);
    }
    return () => clearInterval(sessionRef.current);
  }, [currentUser, screen]);

  const extendSession = () => setSessionTime(SESSION_TIMEOUT);

  const handleLogout = useCallback(
    (reason = 'manual') => {
      if (currentUser) logEvent('LOGOUT', currentUser.name + ' — ' + reason);
      clearInterval(sessionRef.current);
      setCurrentUser(null);
      setLoginKey((k) => k + 1);
      setDrawerOpen(false);
      setSupportOpen(false);
      setScreen('login');
      if (reason === 'timeout')
        Alert.alert(
          'Session Expired',
          'You have been logged out due to inactivity.'
        );
    },
    [currentUser]
  );

  const goTo = (s) => {
    setScreen(s);
    setDrawerOpen(false);
  };

  const canAccess = (target) => {
    if (!currentUser) return false;
    return currentUser.access?.includes(target) || currentUser.role === 'admin';
  };

  return (
    <View style={styles.app}>
      {screen === 'login' && (
        <LoginScreen
          key={loginKey}
          setScreen={setScreen}
          setCurrentUser={setCurrentUser}
        />
      )}

      {screen !== 'login' && currentUser && (
        <>
          <SessionBanner timeLeft={sessionTime} onExtend={extendSession} />
          <MenuDrawer
            visible={drawerOpen}
            onClose={() => setDrawerOpen(false)}
            screen={screen}
            setScreenFn={goTo}
            handleLogout={handleLogout}
            currentUser={currentUser}
          />
          <SupportModal
            visible={supportOpen}
            onClose={() => setSupportOpen(false)}
            currentUser={currentUser}
          />
        </>
      )}

      {screen === 'admin' && canAccess('admin') && (
        <AdminDashboard
          setScreen={setScreen}
          currentUser={currentUser}
          onMenu={() => setDrawerOpen(true)}
          onSupport={() => setSupportOpen(true)}
        />
      )}
      {screen === 'manager' && canAccess('manager') && (
        <ManagerDashboard
          setScreen={setScreen}
          currentUser={currentUser}
          onMenu={() => setDrawerOpen(true)}
          onSupport={() => setSupportOpen(true)}
        />
      )}
      {screen === 'chef' && canAccess('chef') && (
        <ChefDashboard
          setScreen={setScreen}
          currentUser={currentUser}
          onMenu={() => setDrawerOpen(true)}
          onSupport={() => setSupportOpen(true)}
        />
      )}
      {screen === 'staff' && canAccess('staff') && (
        <StaffDashboard
          setScreen={setScreen}
          currentUser={currentUser}
          onMenu={() => setDrawerOpen(true)}
          onSupport={() => setSupportOpen(true)}
        />
      )}
      {screen === 'analytics' && canAccess('analytics') && (
        <AnalyticsDashboard
          setScreen={setScreen}
          currentUser={currentUser}
          onMenu={() => setDrawerOpen(true)}
          onSupport={() => setSupportOpen(true)}
        />
      )}
      {screen === 'security' && canAccess('security') && (
        <SecurityDashboard
          setScreen={setScreen}
          currentUser={currentUser}
          onMenu={() => setDrawerOpen(true)}
          onSupport={() => setSupportOpen(true)}
        />
      )}
      {screen === 'guest' && (
        <GuestApp
          setScreen={setScreen}
          onSupport={() => setSupportOpen(true)}
        />
      )}

      {/* Unauthorized */}
      {screen !== 'login' &&
        screen !== 'guest' &&
        (!currentUser || !canAccess(screen)) && (
          <View style={[styles.center, { backgroundColor: BG }]}>
            <HotelBg />
            <Ionicons name="lock-closed" size={48} color={DANGER} />
            <Text
              style={{
                color: DANGER,
                fontSize: 18,
                fontWeight: 'bold',
                marginTop: 12,
              }}>
              Access Denied
            </Text>
            <Text
              style={{
                color: MUTED,
                fontSize: 13,
                marginTop: 6,
                textAlign: 'center',
                paddingHorizontal: 30,
              }}>
              Your role does not have permission to access this area.
            </Text>
            <TouchableOpacity
              style={[styles.mainBtn, { marginTop: 24 }]}
              onPress={() => setScreen(currentUser?.role || 'login')}>
              <Text style={styles.btnText}>Go to My Dashboard</Text>
            </TouchableOpacity>
          </View>
        )}
    </View>
  );
}

/* ─── LOGIN SCREEN ────────────────────────────────────────────────────────────── */
function LoginScreen({ setScreen, setCurrentUser }) {
  const [loginType, setLoginType] = useState('staff');
  const [staffId, setStaffId] = useState('');
  const [pin, setPin] = useState('');
  const [showPin, setShowPin] = useState(false);
  const [errors, setErrors] = useState({});
  const [loading, setLoading] = useState(false);
  const [attempts, setAttempts] = useState(0);
  const [lockedOut, setLockedOut] = useState(false);
  const [lockTimer, setLockTimer] = useState(0);
  const [showCredHelper, setShowCredHelper] = useState(false);
  const shakeAnim = useRef(new Animated.Value(0)).current;

  useEffect(() => {
    let interval;
    if (lockedOut && lockTimer > 0) {
      interval = setInterval(() => {
        setLockTimer((t) => {
          if (t <= 1) {
            setLockedOut(false);
            setAttempts(0);
            clearInterval(interval);
            return 0;
          }
          return t - 1;
        });
      }, 1000);
    }
    return () => clearInterval(interval);
  }, [lockedOut, lockTimer]);

  const shake = () => {
    Vibration.vibrate(200);
    Animated.sequence([
      Animated.timing(shakeAnim, {
        toValue: 10,
        duration: 50,
        useNativeDriver: true,
      }),
      Animated.timing(shakeAnim, {
        toValue: -10,
        duration: 50,
        useNativeDriver: true,
      }),
      Animated.timing(shakeAnim, {
        toValue: 10,
        duration: 50,
        useNativeDriver: true,
      }),
      Animated.timing(shakeAnim, {
        toValue: 0,
        duration: 50,
        useNativeDriver: true,
      }),
    ]).start();
  };

  const handleStaffLogin = () => {
    if (lockedOut) return;
    const e = {};
    if (!staffId.trim()) e.staffId = 'Staff ID is required.';
    if (!pin.trim()) e.pin = 'PIN is required.';
    else if (pin.length < 4) e.pin = 'PIN must be 4 digits.';
    setErrors(e);
    if (Object.keys(e).length > 0) {
      shake();
      return;
    }

    setLoading(true);
    setTimeout(() => {
      const user = STAFF_CREDENTIALS.find(
        (u) =>
          u.id.toLowerCase() === staffId.trim().toLowerCase() &&
          u.pin === pin.trim()
      );
      setLoading(false);
      if (user) {
        setAttempts(0);
        logEvent('LOGIN_SUCCESS', user.name + ' (' + user.id + ')');
        setCurrentUser(user);
        setScreen(user.role === 'analytics' ? 'analytics' : user.role);
      } else {
        const next = attempts + 1;
        setAttempts(next);
        logEvent('LOGIN_FAIL', 'ID: ' + staffId + ' — attempt ' + next);
        shake();
        if (next >= MAX_ATTEMPTS) {
          setLockedOut(true);
          setLockTimer(LOCKOUT_SECONDS);
          setErrors({
            pin:
              'Too many failed attempts. Locked for ' + LOCKOUT_SECONDS + 's.',
          });
          logEvent('ACCOUNT_LOCKED', staffId);
        } else {
          setErrors({
            pin:
              'Invalid ID or PIN. ' +
              (MAX_ATTEMPTS - next) +
              ' attempt(s) remaining.',
          });
        }
        setPin('');
      }
    }, 900);
  };

  /* Role credential helper — shows what ID to use per role */
  const roleHints = [
    { role: 'admin', id: 'ADM-001', name: 'ROOT REAPER', color: GOLD },
    { role: 'manager', id: 'MGR-001', name: 'NS-MAYCEE', color: GREEN },
    { role: 'chef', id: 'CHF-001', name: 'KARANJA DICKSON', color: AMBER },
    { role: 'staff', id: 'STF-001', name: 'LINKEN SCOFIELD', color: ACCENT },
    { role: 'analytics', id: 'ANA-001', name: 'MWEMBI MAURICE', color: PURPLE },
    { role: 'security', id: 'SEC-001', name: 'PURITY OMUNGE', color: DANGER },
  ];

  return (
    <KeyboardAvoidingView
      style={{ flex: 1 }}
      behavior={Platform.OS === 'ios' ? 'padding' : undefined}>
      <ScrollView
        contentContainerStyle={[styles.center, { paddingVertical: 40 }]}>
        <HotelBg />

        {/* Tab Toggle */}
        <View
          style={{
            flexDirection: 'row',
            marginBottom: 28,
            backgroundColor: CARD,
            borderRadius: 12,
            padding: 4,
          }}>
          {['staff', 'guest'].map((t) => (
            <TouchableOpacity
              key={t}
              onPress={() => setLoginType(t)}
              style={{
                paddingHorizontal: 28,
                paddingVertical: 9,
                borderRadius: 10,
                backgroundColor: loginType === t ? GOLD : 'transparent',
              }}>
              <Text
                style={{
                  color: loginType === t ? '#1a1200' : MUTED,
                  fontWeight: 'bold',
                  fontSize: 13,
                }}>
                {t === 'staff' ? 'Staff Login' : 'Guest'}
              </Text>
            </TouchableOpacity>
          ))}
        </View>

        {/* Logo */}
        <View style={styles.logoWrap}>
          <Ionicons
            name="diamond-outline"
            size={30}
            color={GOLD}
            style={{ marginBottom: 4 }}
          />
          <Text style={styles.logo}>NEXA</Text>
          <Text style={styles.subtitle}>HOSPITALITY MANAGEMENT</Text>
          <View style={styles.logoDivider} />
        </View>

        {loginType === 'staff' ? (
          <Animated.View
            style={{ width: 300, transform: [{ translateX: shakeAnim }] }}>
            {/* Lockout Banner */}
            {lockedOut && (
              <View
                style={{
                  backgroundColor: DANGER + '22',
                  borderRadius: 10,
                  padding: 10,
                  marginBottom: 10,
                  borderWidth: 1,
                  borderColor: DANGER + '44',
                  flexDirection: 'row',
                  alignItems: 'center',
                }}>
                <Ionicons name="lock-closed" size={16} color={DANGER} />
                <Text style={{ color: DANGER, fontSize: 12, marginLeft: 8 }}>
                  Account locked. Retry in {lockTimer}s
                </Text>
              </View>
            )}

            {/* Attempt Warning */}
            {attempts > 0 && !lockedOut && (
              <View
                style={{
                  backgroundColor: AMBER + '22',
                  borderRadius: 10,
                  padding: 8,
                  marginBottom: 8,
                  borderWidth: 1,
                  borderColor: AMBER + '44',
                }}>
                <Text
                  style={{ color: AMBER, fontSize: 11, textAlign: 'center' }}>
                  ⚠ Warning: {MAX_ATTEMPTS - attempts} attempt(s) remaining
                  before lockout
                </Text>
              </View>
            )}

            {/* Staff ID */}
            <Text
              style={{
                color: MUTED,
                fontSize: 10,
                marginBottom: 4,
                letterSpacing: 1.5,
              }}>
              STAFF ID
            </Text>
            <View style={styles.inputWrap}>
              <Ionicons
                name="id-card-outline"
                size={18}
                color={GOLD}
                style={styles.inputIcon}
              />
              <TextInput
                placeholder="e.g. NS-M01"
                placeholderTextColor={MUTED}
                style={styles.inputField}
                value={staffId}
                onChangeText={setStaffId}
                autoCapitalize="characters"
                editable={!lockedOut}
              />
            </View>
            {errors.staffId && (
              <Text style={styles.errorText}>{errors.staffId}</Text>
            )}

            {/* PIN */}
            <Text
              style={{
                color: MUTED,
                fontSize: 10,
                marginBottom: 4,
                marginTop: 10,
                letterSpacing: 1.5,
              }}>
              4-DIGIT PIN
            </Text>
            <View style={styles.inputWrap}>
              <Ionicons
                name="keypad-outline"
                size={18}
                color={GOLD}
                style={styles.inputIcon}
              />
              <TextInput
                placeholder="Enter PIN"
                placeholderTextColor={MUTED}
                style={[styles.inputField, { flex: 1 }]}
                value={pin}
                onChangeText={setPin}
                secureTextEntry={!showPin}
                keyboardType="numeric"
                maxLength={4}
                editable={!lockedOut}
              />
              <TouchableOpacity
                onPress={() => setShowPin(!showPin)}
                style={{ paddingRight: 12 }}>
                <Ionicons
                  name={showPin ? 'eye-off-outline' : 'eye-outline'}
                  size={18}
                  color={MUTED}
                />
              </TouchableOpacity>
            </View>
            {errors.pin && <Text style={styles.errorText}>{errors.pin}</Text>}

            {/* Security note */}
            <View
              style={{
                backgroundColor: CARD2,
                borderRadius: 10,
                padding: 10,
                marginTop: 8,
                marginBottom: 4,
              }}>
              <Text style={{ color: MUTED, fontSize: 10, textAlign: 'center' }}>
                🔒 All logins are recorded and audited.{'\n'}Forgotten PIN?
                Contact your administrator.
              </Text>
            </View>

            {/* Secure Login Button */}
            <TouchableOpacity
              style={[
                styles.mainBtn,
                { width: '100%', marginTop: 10, opacity: lockedOut ? 0.5 : 1 },
              ]}
              onPress={handleStaffLogin}
              disabled={loading || lockedOut}>
              {loading ? (
                <ActivityIndicator color="#1a1200" />
              ) : (
                <View style={{ flexDirection: 'row', alignItems: 'center' }}>
                  <Ionicons
                    name="shield-checkmark-outline"
                    size={16}
                    color="#1a1200"
                    style={{ marginRight: 6 }}
                  />
                  <Text style={styles.btnText}>Secure Login</Text>
                </View>
              )}
            </TouchableOpacity>

            {/* Credential Helper (demo aid) */}
            <TouchableOpacity
              onPress={() => setShowCredHelper(!showCredHelper)}
              style={{ marginTop: 16, alignItems: 'center' }}>
              <Text style={{ color: MUTED, fontSize: 11 }}>
                {showCredHelper ? '▲ Hide' : '▼ Show'} Demo Credentials
              </Text>
            </TouchableOpacity>

            {showCredHelper && (
              <View style={{ marginTop: 8 }}>
                <Text
                  style={{
                    color: MUTED,
                    fontSize: 10,
                    marginBottom: 6,
                    textAlign: 'center',
                  }}>
                  Tap a role to auto-fill ID (PIN shown for demo)
                </Text>
                {roleHints.map((r) => (
                  <TouchableOpacity
                    key={r.id}
                    onPress={() => {
                      setStaffId(r.id);
                      setPin(
                        STAFF_CREDENTIALS.find((u) => u.id === r.id)?.pin || ''
                      );
                    }}
                    style={{
                      backgroundColor: CARD2,
                      borderRadius: 10,
                      padding: 10,
                      marginBottom: 6,
                      flexDirection: 'row',
                      alignItems: 'center',
                      borderWidth: 1,
                      borderColor: r.color + '30',
                    }}>
                    <Ionicons
                      name={ROLES[r.role]?.icon || 'person-outline'}
                      size={16}
                      color={r.color}
                    />
                    <View style={{ marginLeft: 10, flex: 1 }}>
                      <Text
                        style={{
                          color: WHITE,
                          fontSize: 12,
                          fontWeight: 'bold',
                        }}>
                        {r.name}
                      </Text>
                      <Text style={{ color: MUTED, fontSize: 10 }}>
                        {r.id + ' • ' + ROLES[r.role]?.label}
                      </Text>
                    </View>
                    <View
                      style={{
                        backgroundColor: r.color + '22',
                        borderRadius: 8,
                        paddingHorizontal: 8,
                        paddingVertical: 3,
                      }}>
                      <Text
                        style={{
                          color: r.color,
                          fontSize: 10,
                          fontWeight: 'bold',
                        }}>
                        PIN: {STAFF_CREDENTIALS.find((u) => u.id === r.id)?.pin}
                      </Text>
                    </View>
                  </TouchableOpacity>
                ))}
              </View>
            )}
          </Animated.View>
        ) : (
          /* GUEST SECTION — no credentials */
          <View style={{ alignItems: 'center', width: 300 }}>
            <View
              style={{
                backgroundColor: CARD2,
                borderRadius: 14,
                padding: 16,
                marginBottom: 20,
                borderWidth: 1,
                borderColor: '#ffffff10',
                width: '100%',
              }}>
              <Text
                style={{
                  color: GOLD,
                  fontWeight: 'bold',
                  fontSize: 14,
                  marginBottom: 6,
                }}>
                Guest Access
              </Text>
              <Text style={{ color: MUTED, fontSize: 12, lineHeight: 18 }}>
                Guests do not require credentials. Enter the portal to book
                tables, reserve rooms, browse the menu, and make payments.
              </Text>
            </View>
            <TouchableOpacity
              style={[styles.mainBtn, { width: '100%' }]}
              onPress={() => setScreen('guest')}>
              <Ionicons
                name="arrow-forward-circle-outline"
                size={18}
                color="#1a1200"
                style={{ marginRight: 8 }}
              />
              <Text style={styles.btnText}>Enter Guest Portal</Text>
            </TouchableOpacity>
            <Text
              style={{
                color: MUTED,
                fontSize: 10,
                marginTop: 14,
                marginBottom: 8,
              }}>
              Social login — coming soon
            </Text>
            <View style={{ flexDirection: 'row' }}>
              {[
                { bg: '#db4437', icon: 'logo-google', label: 'Google' },
                { bg: '#0078D4', icon: 'logo-windows', label: 'Microsoft' },
                { bg: '#000', icon: 'logo-apple', label: 'Apple' },
              ].map((s) => (
                <TouchableOpacity
                  key={s.label}
                  style={[
                    styles.socialBtn,
                    { backgroundColor: s.bg, opacity: 0.4 },
                  ]}>
                  <Ionicons name={s.icon} size={15} color="white" />
                  <Text style={styles.socialText}>{s.label}</Text>
                </TouchableOpacity>
              ))}
            </View>
          </View>
        )}
      </ScrollView>
    </KeyboardAvoidingView>
  );
}

/* ─── STAT CARD ───────────────────────────────────────────────────────────────── */
function Stat({ title, value, color, icon }) {
  return (
    <View style={styles.statCard}>
      {icon && (
        <Ionicons
          name={icon}
          size={16}
          color={color || GOLD}
          style={{ marginBottom: 4 }}
        />
      )}
      <Text style={[styles.statValue, color && { color }]}>{value}</Text>
      <Text style={styles.statTitle}>{title}</Text>
    </View>
  );
}

/* ─── WELCOME CARD (shared) ───────────────────────────────────────────────────── */
function WelcomeCard({ user }) {
  const role = ROLES[user.role];
  return (
    <View
      style={[
        styles.card,
        {
          flexDirection: 'row',
          alignItems: 'center',
          marginTop: 6,
          borderLeftWidth: 3,
          borderLeftColor: role?.color || GOLD,
        },
      ]}>
      <View
        style={{
          backgroundColor: (role?.color || GOLD) + '22',
          borderRadius: 24,
          width: 44,
          height: 44,
          justifyContent: 'center',
          alignItems: 'center',
          marginRight: 12,
        }}>
        <Ionicons
          name={role?.icon || 'person-outline'}
          size={22}
          color={role?.color || GOLD}
        />
      </View>
      <View style={{ flex: 1 }}>
        <Text style={{ color: WHITE, fontWeight: 'bold', fontSize: 15 }}>
          {'Welcome, ' + user.name}
        </Text>
        <Text style={{ color: MUTED, fontSize: 11 }}>
          {user.id + ' • ' + role?.label + ' • ' + user.dept}
        </Text>
      </View>
      <View
        style={{
          backgroundColor: (role?.color || GOLD) + '22',
          borderRadius: 10,
          paddingHorizontal: 8,
          paddingVertical: 4,
        }}>
        <Text
          style={{
            color: role?.color || GOLD,
            fontSize: 9,
            fontWeight: 'bold',
          }}>
          {user.shift}
        </Text>
      </View>
    </View>
  );
}

/* ─── ADMIN DASHBOARD ─────────────────────────────────────────────────────────── */
const INITIAL_BOOKINGS = [
  {
    id: 1,
    name: 'John Doe',
    room: '101',
    time: '2:00 PM',
    status: 'Ongoing',
    type: 'room',
  },
  {
    id: 2,
    name: 'Jane Smith',
    room: '204',
    time: '8:00 PM',
    status: 'Ready',
    type: 'room',
  },
  {
    id: 3,
    name: 'Mark Lee',
    room: 'T-3',
    time: '7:00 PM',
    status: 'Upcoming',
    type: 'table',
  },
  {
    id: 4,
    name: 'Sara Cruz',
    room: 'T-1',
    time: '6:00 PM',
    status: 'Upcoming',
    type: 'table',
  },
  {
    id: 5,
    name: 'Tom Brown',
    room: '305',
    time: '9:00 PM',
    status: 'Ready',
    type: 'room',
  },
];

function AdminDashboard({ setScreen, currentUser, onMenu, onSupport }) {
  const [bookings, setBookings] = useState(INITIAL_BOOKINGS);
  const [search, setSearch] = useState('');
  const [filter, setFilter] = useState('All');
  const [notifs, setNotifs] = useState(3);
  const [showForm, setShowForm] = useState(false);
  const [newName, setNewName] = useState('');
  const [newTime, setNewTime] = useState('');
  const [newRoom, setNewRoom] = useState('');
  const [newStatus, setNewStatus] = useState('Upcoming');
  const [newType, setNewType] = useState('room');

  const filtered = bookings.filter((b) => {
    const ms = b.name.toLowerCase().includes(search.toLowerCase());
    const mf = filter === 'All' || b.status === filter;
    return ms && mf;
  });

  const cancelBooking = (id) => {
    Alert.alert('Cancel Booking', 'Are you sure?', [
      { text: 'No' },
      {
        text: 'Yes, Cancel',
        style: 'destructive',
        onPress: () => {
          setBookings((prev) => prev.filter((b) => b.id !== id));
          logEvent('BOOKING_CANCELLED', 'ID ' + id);
        },
      },
    ]);
  };

  const addBooking = () => {
    if (!newName.trim() || !newTime.trim() || !newRoom.trim()) {
      Alert.alert('Fill all fields.');
      return;
    }
    const nb = {
      id: Date.now(),
      name: newName,
      room: newRoom,
      time: newTime,
      status: newStatus,
      type: newType,
    };
    setBookings((prev) => [nb, ...prev]);
    logEvent('BOOKING_ADDED', newName + ' — ' + newRoom);
    setNewName('');
    setNewTime('');
    setNewRoom('');
    setNewStatus('Upcoming');
    setShowForm(false);
  };

  const statusColor = (s) =>
    s === 'Ongoing' ? AMBER : s === 'Ready' ? GREEN : ACCENT;

  return (
    <ScrollView style={styles.page}>
      <TopBar
        title="Admin"
        onMenu={onMenu}
        onSupport={onSupport}
        notifs={notifs}
        onNotif={() => {
          setNotifs(0);
          Alert.alert('Notifications', '3 new bookings received.');
        }}
        currentUser={currentUser}
      />
      <WelcomeCard user={currentUser} />

      <View style={[styles.statsRow, { marginTop: 12 }]}>
        <Stat
          title="Bookings"
          value={bookings.length.toString()}
          color={GOLD}
          icon="calendar-outline"
        />
        <Stat
          title="Check-ins"
          value="13"
          color={GREEN}
          icon="log-in-outline"
        />
        <Stat
          title="Revenue"
          value="$1.4K"
          color={ACCENT}
          icon="cash-outline"
        />
      </View>

      {/* Quick actions */}
      <View style={styles.card}>
        <Text style={styles.cardTitle}>Quick Actions</Text>
        <View style={{ flexDirection: 'row', flexWrap: 'wrap', gap: 8 }}>
          {[
            {
              label: 'Analytics',
              icon: 'bar-chart-outline',
              target: 'analytics',
              color: PURPLE,
            },
            {
              label: 'Chef View',
              icon: 'restaurant-outline',
              target: 'chef',
              color: AMBER,
            },
            {
              label: 'Staff View',
              icon: 'people-outline',
              target: 'staff',
              color: ACCENT,
            },
            {
              label: 'Security',
              icon: 'lock-closed-outline',
              target: 'security',
              color: DANGER,
            },
            {
              label: 'Manager',
              icon: 'briefcase-outline',
              target: 'manager',
              color: GREEN,
            },
            {
              label: 'Guest App',
              icon: 'person-outline',
              target: 'guest',
              color: MUTED,
            },
          ].map((a) => (
            <TouchableOpacity
              key={a.target}
              onPress={() => setScreen(a.target)}
              style={{
                backgroundColor: a.color + '18',
                borderRadius: 10,
                padding: 10,
                alignItems: 'center',
                width: '30%',
                borderWidth: 1,
                borderColor: a.color + '30',
              }}>
              <Ionicons name={a.icon} size={20} color={a.color} />
              <Text style={{ color: WHITE, fontSize: 10, marginTop: 4 }}>
                {a.label}
              </Text>
            </TouchableOpacity>
          ))}
        </View>
      </View>

      {/* Search + filter */}
      <View style={[styles.inputWrap, { marginTop: 14, width: '100%' }]}>
        <Ionicons
          name="search-outline"
          size={18}
          color={GOLD}
          style={styles.inputIcon}
        />
        <TextInput
          placeholder="Search guest…"
          placeholderTextColor={MUTED}
          style={styles.inputField}
          value={search}
          onChangeText={setSearch}
        />
      </View>
      <ScrollView
        horizontal
        showsHorizontalScrollIndicator={false}
        style={{ marginTop: 8 }}>
        {['All', 'Ongoing', 'Ready', 'Upcoming'].map((f) => (
          <TouchableOpacity
            key={f}
            onPress={() => setFilter(f)}
            style={[styles.chip, filter === f && styles.chipActive]}>
            <Text
              style={[styles.chipText, filter === f && { color: '#1a1200' }]}>
              {f}
            </Text>
          </TouchableOpacity>
        ))}
      </ScrollView>

      {/* Bookings */}
      <View style={styles.card}>
        <View style={styles.cardHeader}>
          <Text style={styles.cardTitle}>Recent Bookings</Text>
          <TouchableOpacity
            onPress={() => setShowForm(!showForm)}
            style={styles.addBtn}>
            <Ionicons name="add" size={18} color="#1a1200" />
            <Text
              style={{ fontWeight: 'bold', fontSize: 11, color: '#1a1200' }}>
              Add
            </Text>
          </TouchableOpacity>
        </View>

        {showForm && (
          <View style={styles.formBox}>
            {[
              { placeholder: 'Guest Name', value: newName, set: setNewName },
              {
                placeholder: 'Room / Table No.',
                value: newRoom,
                set: setNewRoom,
              },
              {
                placeholder: 'Time (e.g. 5:00 PM)',
                value: newTime,
                set: setNewTime,
              },
            ].map((f, i) => (
              <View
                key={i}
                style={[styles.inputWrap, { width: '100%', marginBottom: 8 }]}>
                <TextInput
                  placeholder={f.placeholder}
                  placeholderTextColor={MUTED}
                  style={styles.inputField}
                  value={f.value}
                  onChangeText={f.set}
                />
              </View>
            ))}
            <ScrollView horizontal showsHorizontalScrollIndicator={false}>
              {['Upcoming', 'Ready', 'Ongoing'].map((s) => (
                <TouchableOpacity
                  key={s}
                  onPress={() => setNewStatus(s)}
                  style={[
                    styles.chip,
                    newStatus === s && styles.chipActive,
                    { marginRight: 6 },
                  ]}>
                  <Text
                    style={[
                      styles.chipText,
                      newStatus === s && { color: '#1a1200' },
                    ]}>
                    {s}
                  </Text>
                </TouchableOpacity>
              ))}
            </ScrollView>
            <TouchableOpacity
              style={[styles.mainBtn, { width: '100%', marginTop: 8 }]}
              onPress={addBooking}>
              <Text style={styles.btnText}>Save Booking</Text>
            </TouchableOpacity>
          </View>
        )}

        {filtered.length === 0 ? (
          <Text style={{ color: MUTED, textAlign: 'center', marginTop: 10 }}>
            No bookings found.
          </Text>
        ) : (
          filtered.map((b) => (
            <View key={b.id} style={styles.bookingRow}>
              <View style={{ flex: 1 }}>
                <Text style={styles.rowText}>{b.name}</Text>
                <Text style={{ color: MUTED, fontSize: 11 }}>
                  {b.room + ' • ' + b.time}
                </Text>
              </View>
              <Text
                style={[
                  styles.statusPill,
                  {
                    backgroundColor: statusColor(b.status) + '22',
                    color: statusColor(b.status),
                  },
                ]}>
                {b.status}
              </Text>
              <TouchableOpacity
                onPress={() => cancelBooking(b.id)}
                style={{ marginLeft: 10 }}>
                <Ionicons name="trash-outline" size={18} color={DANGER} />
              </TouchableOpacity>
            </View>
          ))
        )}
      </View>

      <AdminAnalyticsPreview />
    </ScrollView>
  );
}

/* ─── ANALYTICS PREVIEW (inline in admin) ────────────────────────────────────── */
function AdminAnalyticsPreview() {
  const weeklyB = [12, 18, 9, 15, 20, 25, 17];
  const weeklyR = [480, 720, 360, 600, 800, 1000, 680];
  const days = ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'];
  const [metric, setMetric] = useState('bookings');
  const values = metric === 'bookings' ? weeklyB : weeklyR;
  const maxVal = Math.max(...values);
  const BAR_H = 80;

  return (
    <View>
      <View style={[styles.card, { marginTop: 16 }]}>
        <View
          style={{
            flexDirection: 'row',
            justifyContent: 'space-between',
            alignItems: 'center',
            marginBottom: 10,
          }}>
          <Text style={styles.cardTitle}>Weekly Overview</Text>
          <View style={{ flexDirection: 'row' }}>
            {['bookings', 'revenue'].map((m) => (
              <TouchableOpacity
                key={m}
                onPress={() => setMetric(m)}
                style={[
                  styles.chip,
                  metric === m && styles.chipActive,
                  { marginRight: 6, paddingHorizontal: 10, paddingVertical: 3 },
                ]}>
                <Text
                  style={[
                    styles.chipText,
                    metric === m && { color: '#1a1200' },
                    { fontSize: 10 },
                  ]}>
                  {m === 'bookings' ? 'Bookings' : 'Revenue'}
                </Text>
              </TouchableOpacity>
            ))}
          </View>
        </View>
        <View
          style={{
            flexDirection: 'row',
            alignItems: 'flex-end',
            height: BAR_H + 30,
          }}>
          {values.map((val, idx) => {
            const barH = maxVal > 0 ? Math.round((val / maxVal) * BAR_H) : 0;
            const barColor = metric === 'bookings' ? ACCENT : AMBER;
            return (
              <View key={idx} style={{ flex: 1, alignItems: 'center' }}>
                <Text style={{ color: MUTED, fontSize: 7, marginBottom: 2 }}>
                  {metric === 'revenue' ? '$' + val : val}
                </Text>
                <View
                  style={{
                    width: 16,
                    height: barH,
                    backgroundColor: barColor,
                    borderRadius: 4,
                  }}
                />
                <Text style={{ color: MUTED, fontSize: 8, marginTop: 4 }}>
                  {days[idx]}
                </Text>
              </View>
            );
          })}
        </View>
      </View>

      {/* Revenue breakdown */}
      <View style={styles.card}>
        <Text style={styles.cardTitle}>Revenue Breakdown</Text>
        {[
          { label: 'Rooms', pct: 45, color: ACCENT },
          { label: 'Tables', pct: 30, color: GREEN },
          { label: 'F&B', pct: 15, color: AMBER },
          { label: 'Other', pct: 10, color: DANGER },
        ].map((item) => (
          <View key={item.label} style={{ marginBottom: 10 }}>
            <View
              style={{
                flexDirection: 'row',
                justifyContent: 'space-between',
                marginBottom: 4,
              }}>
              <Text style={{ color: WHITE, fontSize: 12 }}>{item.label}</Text>
              <Text
                style={{ color: item.color, fontSize: 12, fontWeight: 'bold' }}>
                {item.pct + '%'}
              </Text>
            </View>
            <View style={{ height: 6, backgroundColor: BG, borderRadius: 4 }}>
              <View
                style={{
                  height: 6,
                  width: item.pct + '%',
                  backgroundColor: item.color,
                  borderRadius: 4,
                }}
              />
            </View>
          </View>
        ))}
      </View>

      {/* Peak hours */}
      <View style={[styles.card, { marginBottom: 30 }]}>
        <Text style={styles.cardTitle}>Peak Hours</Text>
        {[
          { label: 'Dinner Peak', hour: '7:00 PM – 9:00 PM', pct: 100 },
          { label: 'Lunch Rush', hour: '12:00 PM – 2:00 PM', pct: 90 },
          { label: 'Early Evening', hour: '6:00 PM – 7:00 PM', pct: 65 },
          { label: 'Breakfast', hour: '8:00 AM – 10:00 AM', pct: 40 },
        ].map((ph) => (
          <View key={ph.label} style={{ marginBottom: 10 }}>
            <View
              style={{
                flexDirection: 'row',
                justifyContent: 'space-between',
                marginBottom: 4,
              }}>
              <View>
                <Text
                  style={{ color: WHITE, fontSize: 12, fontWeight: 'bold' }}>
                  {ph.label}
                </Text>
                <Text style={{ color: MUTED, fontSize: 10 }}>{ph.hour}</Text>
              </View>
              <Text style={{ color: GOLD, fontWeight: 'bold', fontSize: 12 }}>
                {ph.pct + '%'}
              </Text>
            </View>
            <View style={{ height: 6, backgroundColor: BG, borderRadius: 4 }}>
              <View
                style={{
                  height: 6,
                  width: ph.pct + '%',
                  backgroundColor: GOLD,
                  borderRadius: 4,
                }}
              />
            </View>
          </View>
        ))}
      </View>
    </View>
  );
}

/* ─── MANAGER DASHBOARD ───────────────────────────────────────────────────────── */
function ManagerDashboard({ setScreen, currentUser, onMenu, onSupport }) {
  const [notifs, setNotifs] = useState(2);
  const [shiftsVisible, setShiftsVisible] = useState(false);

  const shifts = [
    {
      name: 'Sarah Johnson',
      id: 'ADM-001',
      role: 'Admin',
      shift: 'All Day',
      status: 'On Duty',
    },
    {
      name: 'Marco Rossi',
      id: 'CHF-001',
      role: 'Chef',
      shift: '7AM–4PM',
      status: 'On Duty',
    },
    {
      name: 'Aisha Kimani',
      id: 'CHF-002',
      role: 'Chef',
      shift: '3PM–12AM',
      status: 'Off Duty',
    },
    {
      name: 'Carlos Mendez',
      id: 'STF-001',
      role: 'Staff',
      shift: 'Morning',
      status: 'On Duty',
    },
    {
      name: 'Diana Omondi',
      id: 'STF-002',
      role: 'Staff',
      shift: 'Afternoon',
      status: 'Off Duty',
    },
    {
      name: 'Felix Otieno',
      id: 'SEC-001',
      role: 'Security',
      shift: 'Night',
      status: 'Standby',
    },
    {
      name: 'James Waweru',
      id: 'ANA-001',
      role: 'Analytics',
      shift: 'Flexible',
      status: 'On Duty',
    },
  ];

  const tasks = [
    { task: 'Review weekend booking report', due: 'Today', done: false },
    { task: 'Approve kitchen supply order', due: 'Today', done: true },
    { task: 'Staff performance review — Q2', due: 'Friday', done: false },
    { task: 'Inspect VIP suite 401', due: 'Tomorrow', done: false },
    { task: 'Submit monthly revenue summary', due: 'Monday', done: false },
  ];
  const [taskStates, setTaskStates] = useState(tasks.map((t) => t.done));

  return (
    <ScrollView style={styles.page}>
      <TopBar
        title="Manager"
        onMenu={onMenu}
        onSupport={onSupport}
        notifs={notifs}
        onNotif={() => {
          setNotifs(0);
          Alert.alert('2 pending approvals.');
        }}
        currentUser={currentUser}
      />
      <WelcomeCard user={currentUser} />

      <View style={[styles.statsRow, { marginTop: 12 }]}>
        <Stat title="Staff On" value="4" color={GREEN} icon="people-outline" />
        <Stat
          title="Open Tasks"
          value={taskStates.filter((d, i) => !d).length.toString()}
          color={AMBER}
          icon="checkmark-circle-outline"
        />
        <Stat
          title="Alerts"
          value="2"
          color={DANGER}
          icon="alert-circle-outline"
        />
      </View>

      {/* Staff Roster */}
      <View style={styles.card}>
        <TouchableOpacity
          onPress={() => setShiftsVisible(!shiftsVisible)}
          style={styles.cardHeader}>
          <Text style={styles.cardTitle}>Staff Roster</Text>
          <Ionicons
            name={shiftsVisible ? 'chevron-up-outline' : 'chevron-down-outline'}
            size={18}
            color={MUTED}
          />
        </TouchableOpacity>
        {shiftsVisible &&
          shifts.map((s) => {
            const col =
              s.status === 'On Duty'
                ? GREEN
                : s.status === 'Standby'
                ? AMBER
                : MUTED;
            return (
              <View key={s.id} style={styles.bookingRow}>
                <View style={{ flex: 1 }}>
                  <Text style={styles.rowText}>{s.name}</Text>
                  <Text style={{ color: MUTED, fontSize: 10 }}>
                    {s.id + ' • ' + s.role + ' • ' + s.shift}
                  </Text>
                </View>
                <View
                  style={{
                    backgroundColor: col + '22',
                    borderRadius: 10,
                    paddingHorizontal: 8,
                    paddingVertical: 3,
                  }}>
                  <Text
                    style={{ color: col, fontSize: 10, fontWeight: 'bold' }}>
                    {s.status}
                  </Text>
                </View>
              </View>
            );
          })}
      </View>

      {/* Tasks */}
      <View style={[styles.card, { marginBottom: 30 }]}>
        <Text style={styles.cardTitle}>Manager Tasks</Text>
        {tasks.map((t, i) => (
          <TouchableOpacity
            key={i}
            onPress={() =>
              setTaskStates((prev) => {
                const n = [...prev];
                n[i] = !n[i];
                return n;
              })
            }
            style={{
              flexDirection: 'row',
              alignItems: 'center',
              paddingVertical: 10,
              borderBottomWidth: 1,
              borderBottomColor: '#ffffff08',
            }}>
            <Ionicons
              name={taskStates[i] ? 'checkmark-circle' : 'ellipse-outline'}
              size={20}
              color={taskStates[i] ? GREEN : MUTED}
            />
            <View style={{ flex: 1, marginLeft: 10 }}>
              <Text
                style={{
                  color: taskStates[i] ? MUTED : WHITE,
                  fontSize: 13,
                  textDecorationLine: taskStates[i] ? 'line-through' : 'none',
                }}>
                {t.task}
              </Text>
              <Text style={{ color: MUTED, fontSize: 10 }}>Due: {t.due}</Text>
            </View>
          </TouchableOpacity>
        ))}
      </View>
    </ScrollView>
  );
}

/* ─── CHEF DASHBOARD ──────────────────────────────────────────────────────────── */
const INITIAL_ORDERS = [
  {
    id: 1,
    item: 'Chicken Fried Rice',
    table: 'Table 3',
    priority: 'Urgent',
    orderStatus: 'In Progress',
    elapsed: 0,
    allergens: 'Nuts',
  },
  {
    id: 2,
    item: 'Salad + Water',
    table: 'Table 1',
    priority: 'Normal',
    orderStatus: 'In Progress',
    elapsed: 0,
    allergens: '',
  },
  {
    id: 3,
    item: 'Grilled Salmon',
    table: 'Table 5',
    priority: 'Urgent',
    orderStatus: 'In Progress',
    elapsed: 0,
    allergens: 'Fish',
  },
  {
    id: 4,
    item: 'Pasta Carbonara',
    table: 'Table 2',
    priority: 'Normal',
    orderStatus: 'In Progress',
    elapsed: 0,
    allergens: 'Gluten, Dairy',
  },
];

function formatTime(secs) {
  const m = Math.floor(secs / 60)
    .toString()
    .padStart(2, '0');
  const s = (secs % 60).toString().padStart(2, '0');
  return m + ':' + s;
}

function ChefDashboard({ setScreen, currentUser, onMenu, onSupport }) {
  const [orders, setOrders] = useState(INITIAL_ORDERS);
  const [filterStatus, setFilterStatus] = useState('All');

  useEffect(() => {
    const interval = setInterval(() => {
      setOrders((prev) =>
        prev.map((o) =>
          o.orderStatus === 'In Progress' ? { ...o, elapsed: o.elapsed + 1 } : o
        )
      );
    }, 1000);
    return () => clearInterval(interval);
  }, []);

  const markDone = (id) => {
    setOrders((prev) =>
      prev.map((o) => (o.id === id ? { ...o, orderStatus: 'Done' } : o))
    );
    logEvent('ORDER_DONE', 'Order ID ' + id);
  };

  const filtered =
    filterStatus === 'All'
      ? orders
      : orders.filter((o) => o.orderStatus === filterStatus);

  return (
    <ScrollView style={styles.page}>
      <TopBar
        title="Chef"
        onMenu={onMenu}
        onSupport={onSupport}
        currentUser={currentUser}
      />
      <WelcomeCard user={currentUser} />

      <View style={[styles.statsRow, { marginTop: 12 }]}>
        <Stat
          title="Urgent"
          value={orders
            .filter((o) => o.priority === 'Urgent' && o.orderStatus !== 'Done')
            .length.toString()}
          color={DANGER}
          icon="flame-outline"
        />
        <Stat
          title="In Progress"
          value={orders
            .filter((o) => o.orderStatus === 'In Progress')
            .length.toString()}
          color={AMBER}
          icon="timer-outline"
        />
        <Stat
          title="Done"
          value={orders
            .filter((o) => o.orderStatus === 'Done')
            .length.toString()}
          color={GREEN}
          icon="checkmark-circle-outline"
        />
      </View>

      <ScrollView
        horizontal
        showsHorizontalScrollIndicator={false}
        style={{ marginTop: 12 }}>
        {['All', 'In Progress', 'Done'].map((f) => (
          <TouchableOpacity
            key={f}
            onPress={() => setFilterStatus(f)}
            style={[styles.chip, filterStatus === f && styles.chipActive]}>
            <Text
              style={[
                styles.chipText,
                filterStatus === f && { color: '#1a1200' },
              ]}>
              {f}
            </Text>
          </TouchableOpacity>
        ))}
      </ScrollView>

      {filtered.map((order) => {
        const isUrgent = order.priority === 'Urgent';
        const isDone = order.orderStatus === 'Done';
        const isOverdue = order.elapsed > 900;
        return (
          <View
            key={order.id}
            style={[
              styles.card,
              isUrgent &&
                !isDone && { borderLeftWidth: 4, borderLeftColor: DANGER },
              isDone && { opacity: 0.6 },
            ]}>
            <View style={styles.cardHeader}>
              <View style={{ flex: 1 }}>
                <Text
                  style={[
                    styles.rowText,
                    { fontSize: 15, fontWeight: 'bold' },
                  ]}>
                  {order.item}
                </Text>
                <Text style={{ color: MUTED, fontSize: 12, marginTop: 2 }}>
                  {order.table}
                </Text>
                {order.allergens ? (
                  <View
                    style={{
                      flexDirection: 'row',
                      alignItems: 'center',
                      marginTop: 4,
                    }}>
                    <Ionicons name="warning-outline" size={12} color={AMBER} />
                    <Text style={{ color: AMBER, fontSize: 10, marginLeft: 4 }}>
                      Allergens: {order.allergens}
                    </Text>
                  </View>
                ) : null}
              </View>
              <View
                style={{
                  backgroundColor: isUrgent ? DANGER + '22' : GREEN + '22',
                  borderRadius: 12,
                  paddingHorizontal: 8,
                  paddingVertical: 3,
                }}>
                <Text
                  style={{
                    color: isUrgent ? DANGER : GREEN,
                    fontSize: 11,
                    fontWeight: 'bold',
                  }}>
                  {isUrgent ? '🔴 Urgent' : '🟢 Normal'}
                </Text>
              </View>
            </View>
            <View
              style={{
                flexDirection: 'row',
                alignItems: 'center',
                marginTop: 8,
                marginBottom: 10,
              }}>
              <Ionicons
                name="time-outline"
                size={14}
                color={isDone ? GREEN : isOverdue ? DANGER : MUTED}
              />
              <Text
                style={{
                  color: isDone ? GREEN : isOverdue ? DANGER : MUTED,
                  fontSize: 13,
                  marginLeft: 4,
                }}>
                {isDone
                  ? '✓ Completed'
                  : formatTime(order.elapsed) +
                    (isOverdue ? '  ⚠ Overdue' : '')}
              </Text>
            </View>
            {!isDone && (
              <View style={{ flexDirection: 'row' }}>
                <TouchableOpacity
                  style={[styles.orderBtnGreen, { marginRight: 8 }]}
                  onPress={() => markDone(order.id)}>
                  <Ionicons
                    name="checkmark-circle-outline"
                    size={16}
                    color={GREEN}
                  />
                  <Text style={[styles.orderBtnText, { color: GREEN }]}>
                    {' '}
                    Mark Done
                  </Text>
                </TouchableOpacity>
                <TouchableOpacity style={styles.orderBtnAmber}>
                  <Ionicons name="flame-outline" size={16} color={AMBER} />
                  <Text style={[styles.orderBtnText, { color: AMBER }]}>
                    {' '}
                    Cooking
                  </Text>
                </TouchableOpacity>
              </View>
            )}
          </View>
        );
      })}
    </ScrollView>
  );
}

/* ─── STAFF DASHBOARD ─────────────────────────────────────────────────────────── */
const STAFF_MEMBERS = ['Alice', 'Bob', 'Carlos', 'Diana'];
const INITIAL_TABLES = [
  {
    id: 1,
    name: 'Table 1',
    tableStatus: 'Available',
    assignedTo: null,
    billCalled: false,
  },
  {
    id: 2,
    name: 'Table 2',
    tableStatus: 'Busy',
    assignedTo: 'Alice',
    billCalled: false,
  },
  {
    id: 3,
    name: 'Table 3',
    tableStatus: 'Busy',
    assignedTo: 'Bob',
    billCalled: true,
  },
  {
    id: 4,
    name: 'Table 4',
    tableStatus: 'Cleaning',
    assignedTo: 'Carlos',
    billCalled: false,
  },
  {
    id: 5,
    name: 'Table 5',
    tableStatus: 'Available',
    assignedTo: null,
    billCalled: false,
  },
  {
    id: 6,
    name: 'Table 6',
    tableStatus: 'Busy',
    assignedTo: 'Diana',
    billCalled: false,
  },
];

function StaffDashboard({ setScreen, currentUser, onMenu, onSupport }) {
  const [tables, setTables] = useState(INITIAL_TABLES);
  const [assignPicker, setAssignPicker] = useState(null);

  const updateTable = (id, patch) =>
    setTables((prev) =>
      prev.map((t) => (t.id === id ? { ...t, ...patch } : t))
    );
  const markCleaned = (id) => {
    updateTable(id, {
      tableStatus: 'Available',
      assignedTo: null,
      billCalled: false,
    });
    logEvent('TABLE_CLEANED', 'Table ' + id);
  };
  const callBill = (id) => {
    updateTable(id, { billCalled: true });
    logEvent('BILL_CALLED', 'Table ' + id);
    Alert.alert('Bill Requested', 'Bill called for Table ' + id + '.');
  };
  const assignStaff = (tid, staff) => {
    updateTable(tid, { assignedTo: staff, tableStatus: 'Busy' });
    setAssignPicker(null);
    logEvent('STAFF_ASSIGNED', staff + ' → Table ' + tid);
  };
  const statusColor = (s) =>
    s === 'Available' ? GREEN : s === 'Cleaning' ? AMBER : DANGER;

  return (
    <ScrollView style={styles.page}>
      <TopBar
        title="Staff"
        onMenu={onMenu}
        onSupport={onSupport}
        currentUser={currentUser}
      />
      <WelcomeCard user={currentUser} />

      <View style={[styles.statsRow, { marginTop: 12 }]}>
        <Stat
          title="Busy"
          value={tables
            .filter((t) => t.tableStatus === 'Busy')
            .length.toString()}
          color={DANGER}
          icon="people-outline"
        />
        <Stat
          title="Available"
          value={tables
            .filter((t) => t.tableStatus === 'Available')
            .length.toString()}
          color={GREEN}
          icon="checkmark-circle-outline"
        />
        <Stat
          title="Cleaning"
          value={tables
            .filter((t) => t.tableStatus === 'Cleaning')
            .length.toString()}
          color={AMBER}
          icon="sparkles-outline"
        />
      </View>

      {tables.map((table) => {
        const color = statusColor(table.tableStatus);
        return (
          <View
            key={table.id}
            style={[
              styles.card,
              { borderLeftWidth: 4, borderLeftColor: color },
            ]}>
            <View style={styles.cardHeader}>
              <Text
                style={[styles.rowText, { fontSize: 15, fontWeight: 'bold' }]}>
                {table.name}
              </Text>
              <View
                style={{
                  backgroundColor: color + '22',
                  borderRadius: 12,
                  paddingHorizontal: 8,
                  paddingVertical: 3,
                }}>
                <Text style={{ color, fontSize: 11, fontWeight: 'bold' }}>
                  {table.tableStatus}
                </Text>
              </View>
            </View>
            <View
              style={{
                flexDirection: 'row',
                alignItems: 'center',
                marginTop: 4,
                marginBottom: 10,
              }}>
              <Ionicons name="person-outline" size={14} color={MUTED} />
              <Text style={{ color: MUTED, fontSize: 12, marginLeft: 4 }}>
                {table.assignedTo
                  ? 'Assigned: ' + table.assignedTo
                  : 'Unassigned'}
              </Text>
            </View>
            {assignPicker === table.id && (
              <View style={styles.formBox}>
                <Text style={{ color: MUTED, fontSize: 12, marginBottom: 6 }}>
                  Select staff member:
                </Text>
                <View style={{ flexDirection: 'row', flexWrap: 'wrap' }}>
                  {STAFF_MEMBERS.map((s) => (
                    <TouchableOpacity
                      key={s}
                      onPress={() => assignStaff(table.id, s)}
                      style={[
                        styles.chip,
                        table.assignedTo === s && styles.chipActive,
                        { marginBottom: 6, marginRight: 6 },
                      ]}>
                      <Text
                        style={[
                          styles.chipText,
                          table.assignedTo === s && { color: '#1a1200' },
                        ]}>
                        {s}
                      </Text>
                    </TouchableOpacity>
                  ))}
                </View>
              </View>
            )}
            <View style={{ flexDirection: 'row', flexWrap: 'wrap' }}>
              <TouchableOpacity
                style={[
                  styles.orderBtnBlue,
                  { marginRight: 6, marginBottom: 6 },
                ]}
                onPress={() =>
                  setAssignPicker(assignPicker === table.id ? null : table.id)
                }>
                <Ionicons name="person-add-outline" size={14} color={ACCENT} />
                <Text style={[styles.orderBtnText, { color: ACCENT }]}>
                  {' '}
                  Assign
                </Text>
              </TouchableOpacity>
              {table.tableStatus !== 'Available' && (
                <TouchableOpacity
                  style={[
                    styles.orderBtnGreen,
                    { marginRight: 6, marginBottom: 6 },
                  ]}
                  onPress={() => markCleaned(table.id)}>
                  <Ionicons name="sparkles-outline" size={14} color={GREEN} />
                  <Text style={[styles.orderBtnText, { color: GREEN }]}>
                    {' '}
                    Mark Clean
                  </Text>
                </TouchableOpacity>
              )}
              {table.tableStatus === 'Busy' && (
                <TouchableOpacity
                  style={
                    table.billCalled ? styles.orderBtnAmber : styles.orderBtnRed
                  }
                  onPress={() => !table.billCalled && callBill(table.id)}
                  disabled={table.billCalled}>
                  <Ionicons
                    name="receipt-outline"
                    size={14}
                    color={table.billCalled ? AMBER : DANGER}
                  />
                  <Text
                    style={[
                      styles.orderBtnText,
                      { color: table.billCalled ? AMBER : DANGER },
                    ]}>
                    {table.billCalled ? '  Bill Called ✓' : '  Call Bill'}
                  </Text>
                </TouchableOpacity>
              )}
            </View>
          </View>
        );
      })}
    </ScrollView>
  );
}

/* ─── ANALYTICS DASHBOARD ─────────────────────────────────────────────────────── */
const ANALYTICS_DATA = {
  weekly: {
    bookings: [12, 18, 9, 15, 20, 25, 17],
    revenue: [480, 720, 360, 600, 800, 1000, 680],
    labels: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
  },
  monthly: {
    bookings: [80, 95, 110, 130, 120, 140, 160, 155, 170, 145, 190, 210],
    revenue: [
      3200, 3800, 4400, 5200, 4800, 5600, 6400, 6200, 6800, 5800, 7600, 8400,
    ],
    labels: [
      'Jan',
      'Feb',
      'Mar',
      'Apr',
      'May',
      'Jun',
      'Jul',
      'Aug',
      'Sep',
      'Oct',
      'Nov',
      'Dec',
    ],
  },
  daily: {
    bookings: [2, 4, 1, 5, 3, 6, 4, 7, 5, 3, 2, 4],
    revenue: [80, 160, 40, 200, 120, 240, 160, 280, 200, 120, 80, 160],
    labels: [
      '6a',
      '7a',
      '8a',
      '9a',
      '10a',
      '11a',
      '12p',
      '1p',
      '2p',
      '3p',
      '4p',
      '5p',
    ],
  },
};

function AnalyticsDashboard({ setScreen, currentUser, onMenu, onSupport }) {
  const [period, setPeriod] = useState('weekly');
  const [metric, setMetric] = useState('bookings');

  const dataset = ANALYTICS_DATA[period];
  const values = dataset[metric];
  const labels = dataset.labels;
  const maxVal = Math.max(...values);
  const BAR_H = 120;

  const totalB = ANALYTICS_DATA.weekly.bookings.reduce((a, b) => a + b, 0);
  const totalR = ANALYTICS_DATA.weekly.revenue.reduce((a, b) => a + b, 0);

  return (
    <ScrollView style={styles.page}>
      <TopBar
        title="Analytics"
        onMenu={onMenu}
        onSupport={onSupport}
        currentUser={currentUser}
      />
      <WelcomeCard user={currentUser} />

      <View style={[styles.statsRow, { marginTop: 12 }]}>
        <Stat
          title="Bookings"
          value={totalB.toString()}
          color={GOLD}
          icon="calendar-outline"
        />
        <Stat
          title="Revenue"
          value={'$' + (totalR / 1000).toFixed(1) + 'K'}
          color={GREEN}
          icon="cash-outline"
        />
        <Stat
          title="Avg/Day"
          value={Math.round(totalB / 7).toString()}
          color={ACCENT}
          icon="trending-up-outline"
        />
      </View>

      <View style={{ flexDirection: 'row', marginTop: 14, flexWrap: 'wrap' }}>
        {['daily', 'weekly', 'monthly'].map((p) => (
          <TouchableOpacity
            key={p}
            onPress={() => setPeriod(p)}
            style={[
              styles.chip,
              period === p && styles.chipActive,
              { marginRight: 8, marginBottom: 8 },
            ]}>
            <Text
              style={[styles.chipText, period === p && { color: '#1a1200' }]}>
              {p.charAt(0).toUpperCase() + p.slice(1)}
            </Text>
          </TouchableOpacity>
        ))}
        {['bookings', 'revenue'].map((m) => (
          <TouchableOpacity
            key={m}
            onPress={() => setMetric(m)}
            style={[
              styles.chip,
              metric === m &&
                (m === 'revenue'
                  ? { backgroundColor: AMBER, borderColor: AMBER }
                  : styles.chipActive),
              { marginRight: 8, marginBottom: 8 },
            ]}>
            <Text
              style={[styles.chipText, metric === m && { color: '#1a1200' }]}>
              {m.charAt(0).toUpperCase() + m.slice(1)}
            </Text>
          </TouchableOpacity>
        ))}
      </View>

      <View style={styles.card}>
        <Text style={styles.cardTitle}>
          {period.charAt(0).toUpperCase() +
            period.slice(1) +
            ' ' +
            metric.charAt(0).toUpperCase() +
            metric.slice(1)}
        </Text>
        <View style={{ flexDirection: 'row', marginTop: 10 }}>
          <View
            style={{
              justifyContent: 'space-between',
              height: BAR_H + 10,
              marginRight: 6,
              paddingBottom: 18,
            }}>
            {[maxVal, Math.round(maxVal / 2), 0].map((v, i) => (
              <Text
                key={i}
                style={{ color: MUTED, fontSize: 9, textAlign: 'right' }}>
                {metric === 'revenue' && v > 0 ? '$' + v : v}
              </Text>
            ))}
          </View>
          <ScrollView
            horizontal
            showsHorizontalScrollIndicator={false}
            style={{ flex: 1 }}>
            <View
              style={{
                flexDirection: 'row',
                alignItems: 'flex-end',
                height: BAR_H + 20,
              }}>
              {values.map((val, idx) => {
                const barH =
                  maxVal > 0 ? Math.round((val / maxVal) * BAR_H) : 0;
                const barColor = metric === 'revenue' ? AMBER : ACCENT;
                return (
                  <View
                    key={idx}
                    style={{
                      alignItems: 'center',
                      marginHorizontal: 4,
                      width: 28,
                    }}>
                    <Text
                      style={{ color: MUTED, fontSize: 7, marginBottom: 2 }}>
                      {metric === 'revenue' ? '$' + val : val}
                    </Text>
                    <View
                      style={{
                        width: 18,
                        height: barH,
                        backgroundColor: barColor,
                        borderRadius: 4,
                      }}
                    />
                    <Text style={{ color: MUTED, fontSize: 8, marginTop: 4 }}>
                      {labels[idx]}
                    </Text>
                  </View>
                );
              })}
            </View>
          </ScrollView>
        </View>
      </View>

      {/* Revenue breakdown */}
      <View style={styles.card}>
        <Text style={styles.cardTitle}>Revenue Breakdown</Text>
        {[
          { label: 'Room Bookings', pct: 45, color: ACCENT },
          { label: 'Table Bookings', pct: 30, color: GREEN },
          { label: 'F&B', pct: 15, color: AMBER },
          { label: 'Other', pct: 10, color: DANGER },
        ].map((item) => (
          <View key={item.label} style={{ marginBottom: 10 }}>
            <View
              style={{
                flexDirection: 'row',
                justifyContent: 'space-between',
                marginBottom: 4,
              }}>
              <Text style={{ color: WHITE, fontSize: 12 }}>{item.label}</Text>
              <Text
                style={{ color: item.color, fontSize: 12, fontWeight: 'bold' }}>
                {item.pct + '%'}
              </Text>
            </View>
            <View style={{ height: 6, backgroundColor: BG, borderRadius: 4 }}>
              <View
                style={{
                  height: 6,
                  width: item.pct + '%',
                  backgroundColor: item.color,
                  borderRadius: 4,
                }}
              />
            </View>
          </View>
        ))}
      </View>

      <TouchableOpacity
        style={[
          styles.mainBtn,
          { width: '100%', marginTop: 8, marginBottom: 30 },
        ]}
        onPress={() => {
          logEvent('EXPORT', currentUser.name);
          Alert.alert(
            'Report Exported',
            'NEXA Weekly Report saved to downloads.\n\nBookings: ' +
              totalB +
              '\nRevenue: $' +
              totalR +
              '\nPeak: Saturday'
          );
        }}>
        <Ionicons
          name="download-outline"
          size={18}
          color="#1a1200"
          style={{ marginRight: 8 }}
        />
        <Text style={styles.btnText}>Export Report</Text>
      </TouchableOpacity>
    </ScrollView>
  );
}

/* ─── SECURITY DASHBOARD ──────────────────────────────────────────────────────── */
function SecurityDashboard({ setScreen, currentUser, onMenu, onSupport }) {
  const [tab, setTab] = useState('audit');

  const cameraFeeds = [
    { id: 'CAM-01', location: 'Main Lobby', status: 'Live', alert: false },
    { id: 'CAM-02', location: 'Restaurant', status: 'Live', alert: false },
    { id: 'CAM-03', location: 'Car Park', status: 'Live', alert: true },
    { id: 'CAM-04', location: 'Pool Area', status: 'Offline', alert: false },
    { id: 'CAM-05', location: 'Corridor B2', status: 'Live', alert: false },
    { id: 'CAM-06', location: 'Rooftop', status: 'Live', alert: false },
  ];

  const incidentTypes = [
    'Unauthorized Access',
    'Suspicious Activity',
    'Property Damage',
    'Fire/Safety Hazard',
    'Medical Emergency',
    'Theft',
    'Other',
  ];
  const [incidentType, setIncidentType] = useState('');
  const [incidentLoc, setIncidentLoc] = useState('');
  const [incidentDesc, setIncidentDesc] = useState('');

  const submitIncident = () => {
    if (!incidentType || !incidentLoc.trim()) {
      Alert.alert('Fill in incident type and location.');
      return;
    }
    const ref = 'INC-' + Date.now().toString().slice(-6);
    logEvent('INCIDENT_FILED', ref + ' — ' + incidentType);
    Alert.alert(
      'Incident Filed',
      'Ref: ' +
        ref +
        '\nType: ' +
        incidentType +
        '\nLocation: ' +
        incidentLoc +
        '\n\nAll relevant staff have been notified.'
    );
    setIncidentType('');
    setIncidentLoc('');
    setIncidentDesc('');
  };

  return (
    <ScrollView style={styles.page}>
      <TopBar
        title="Security"
        onMenu={onMenu}
        onSupport={onSupport}
        currentUser={currentUser}
      />
      <WelcomeCard user={currentUser} />

      <View style={[styles.statsRow, { marginTop: 12 }]}>
        <Stat
          title="Cameras"
          value={
            cameraFeeds.filter((c) => c.status === 'Live').length +
            '/' +
            cameraFeeds.length
          }
          color={GREEN}
          icon="videocam-outline"
        />
        <Stat
          title="Alerts"
          value={cameraFeeds.filter((c) => c.alert).length.toString()}
          color={DANGER}
          icon="alert-circle-outline"
        />
        <Stat
          title="Log Events"
          value={auditLog.length.toString()}
          color={PURPLE}
          icon="document-text-outline"
        />
      </View>

      {/* Tabs */}
      <ScrollView
        horizontal
        showsHorizontalScrollIndicator={false}
        style={{ marginTop: 12 }}>
        {['audit', 'cameras', 'incident', 'access'].map((t) => (
          <TouchableOpacity
            key={t}
            onPress={() => setTab(t)}
            style={[
              styles.chip,
              tab === t && { backgroundColor: DANGER, borderColor: DANGER },
              { marginRight: 8 },
            ]}>
            <Text style={[styles.chipText, tab === t && { color: WHITE }]}>
              {t === 'audit'
                ? 'Audit Log'
                : t === 'cameras'
                ? 'Cameras'
                : t === 'incident'
                ? 'File Incident'
                : 'Access Control'}
            </Text>
          </TouchableOpacity>
        ))}
      </ScrollView>

      {/* Audit Log */}
      {tab === 'audit' && (
        <View style={styles.card}>
          <Text style={styles.cardTitle}>
            Audit Log ({auditLog.length} events)
          </Text>
          {auditLog.length === 0 && (
            <Text style={{ color: MUTED, textAlign: 'center', marginTop: 10 }}>
              No events recorded yet.
            </Text>
          )}
          {auditLog.slice(0, 20).map((e, i) => (
            <View
              key={i}
              style={{
                paddingVertical: 8,
                borderBottomWidth: 1,
                borderBottomColor: '#ffffff08',
              }}>
              <View
                style={{
                  flexDirection: 'row',
                  justifyContent: 'space-between',
                }}>
                <Text
                  style={{ color: WHITE, fontSize: 12, fontWeight: 'bold' }}>
                  {e.type}
                </Text>
                <Text style={{ color: MUTED, fontSize: 10 }}>{e.time}</Text>
              </View>
              <Text style={{ color: MUTED, fontSize: 11, marginTop: 2 }}>
                {e.detail}
              </Text>
            </View>
          ))}
        </View>
      )}

      {/* Camera Feeds */}
      {tab === 'cameras' && (
        <View style={styles.card}>
          <Text style={styles.cardTitle}>Camera Feeds</Text>
          {cameraFeeds.map((cam) => (
            <View
              key={cam.id}
              style={{
                flexDirection: 'row',
                alignItems: 'center',
                paddingVertical: 10,
                borderBottomWidth: 1,
                borderBottomColor: '#ffffff08',
              }}>
              <Ionicons
                name="videocam-outline"
                size={18}
                color={cam.status === 'Live' ? GREEN : MUTED}
              />
              <View style={{ flex: 1, marginLeft: 10 }}>
                <Text style={{ color: WHITE, fontSize: 13 }}>
                  {cam.location}
                </Text>
                <Text style={{ color: MUTED, fontSize: 10 }}>{cam.id}</Text>
              </View>
              {cam.alert && (
                <View
                  style={{
                    backgroundColor: DANGER + '22',
                    borderRadius: 8,
                    paddingHorizontal: 8,
                    paddingVertical: 3,
                    marginRight: 8,
                  }}>
                  <Text
                    style={{ color: DANGER, fontSize: 10, fontWeight: 'bold' }}>
                    ALERT
                  </Text>
                </View>
              )}
              <View
                style={{
                  backgroundColor:
                    (cam.status === 'Live' ? GREEN : MUTED) + '22',
                  borderRadius: 8,
                  paddingHorizontal: 8,
                  paddingVertical: 3,
                }}>
                <Text
                  style={{
                    color: cam.status === 'Live' ? GREEN : MUTED,
                    fontSize: 10,
                    fontWeight: 'bold',
                  }}>
                  {cam.status}
                </Text>
              </View>
            </View>
          ))}
        </View>
      )}

      {/* File Incident */}
      {tab === 'incident' && (
        <View style={styles.card}>
          <Text style={styles.cardTitle}>File Security Incident</Text>
          <Text style={{ color: MUTED, fontSize: 11, marginBottom: 12 }}>
            Select incident type:
          </Text>
          <View
            style={{
              flexDirection: 'row',
              flexWrap: 'wrap',
              marginBottom: 12,
            }}>
            {incidentTypes.map((it) => (
              <TouchableOpacity
                key={it}
                onPress={() => setIncidentType(it)}
                style={[
                  styles.chip,
                  incidentType === it && {
                    backgroundColor: DANGER,
                    borderColor: DANGER,
                  },
                  { marginBottom: 6, marginRight: 6 },
                ]}>
                <Text
                  style={[
                    styles.chipText,
                    incidentType === it && { color: WHITE },
                    { fontSize: 10 },
                  ]}>
                  {it}
                </Text>
              </TouchableOpacity>
            ))}
          </View>
          <View style={[styles.inputWrap, { width: '100%', marginBottom: 8 }]}>
            <Ionicons
              name="location-outline"
              size={18}
              color={GOLD}
              style={styles.inputIcon}
            />
            <TextInput
              placeholder="Location (e.g. Room 204)"
              placeholderTextColor={MUTED}
              style={styles.inputField}
              value={incidentLoc}
              onChangeText={setIncidentLoc}
            />
          </View>
          <View style={[styles.inputWrap, { width: '100%', marginBottom: 8 }]}>
            <TextInput
              placeholder="Description (optional)…"
              placeholderTextColor={MUTED}
              style={[
                styles.inputField,
                { height: 60, textAlignVertical: 'top' },
              ]}
              multiline
              value={incidentDesc}
              onChangeText={setIncidentDesc}
            />
          </View>
          <TouchableOpacity
            style={[styles.mainBtn, { width: '100%', backgroundColor: DANGER }]}
            onPress={submitIncident}>
            <Ionicons
              name="alert-circle-outline"
              size={16}
              color={WHITE}
              style={{ marginRight: 8 }}
            />
            <Text style={[styles.btnText, { color: WHITE }]}>
              Submit Incident Report
            </Text>
          </TouchableOpacity>
        </View>
      )}

      {/* Access Control */}
      {tab === 'access' && (
        <View style={[styles.card, { marginBottom: 30 }]}>
          <Text style={styles.cardTitle}>Access Control</Text>
          {[
            { zone: 'Executive Floor (5F)', level: 'Admin Only', locked: true },
            { zone: 'Kitchen', level: 'Chef + Admin', locked: false },
            { zone: 'Back Office', level: 'Staff + Admin', locked: false },
            { zone: 'Server Room', level: 'Admin Only', locked: true },
            { zone: 'Car Park B', level: 'All Staff', locked: false },
            { zone: 'Rooftop', level: 'Security + Admin', locked: true },
          ].map((z) => (
            <View
              key={z.zone}
              style={{
                flexDirection: 'row',
                alignItems: 'center',
                paddingVertical: 10,
                borderBottomWidth: 1,
                borderBottomColor: '#ffffff08',
              }}>
              <Ionicons
                name={z.locked ? 'lock-closed-outline' : 'lock-open-outline'}
                size={18}
                color={z.locked ? DANGER : GREEN}
              />
              <View style={{ flex: 1, marginLeft: 10 }}>
                <Text style={{ color: WHITE, fontSize: 13 }}>{z.zone}</Text>
                <Text style={{ color: MUTED, fontSize: 10 }}>{z.level}</Text>
              </View>
              <TouchableOpacity
                style={{
                  backgroundColor: (z.locked ? DANGER : GREEN) + '22',
                  borderRadius: 8,
                  paddingHorizontal: 10,
                  paddingVertical: 4,
                }}
                onPress={() =>
                  Alert.alert(
                    'Access Control',
                    z.zone + ' requires admin override.'
                  )
                }>
                <Text
                  style={{
                    color: z.locked ? DANGER : GREEN,
                    fontSize: 11,
                    fontWeight: 'bold',
                  }}>
                  {z.locked ? 'Locked' : 'Open'}
                </Text>
              </TouchableOpacity>
            </View>
          ))}
        </View>
      )}
    </ScrollView>
  );
}

/* ─── GUEST APP ───────────────────────────────────────────────────────────────── */
const MENU_ITEMS = [
  {
    id: 1,
    name: 'Grilled Chicken',
    price: 12,
    category: 'Mains',
    allergens: 'None',
    popular: true,
  },
  {
    id: 2,
    name: 'Caesar Salad',
    price: 8,
    category: 'Starters',
    allergens: 'Dairy, Eggs',
    popular: false,
  },
  {
    id: 3,
    name: 'Pasta Carbonara',
    price: 14,
    category: 'Mains',
    allergens: 'Gluten, Dairy',
    popular: true,
  },
  {
    id: 4,
    name: 'Chocolate Lava',
    price: 6,
    category: 'Desserts',
    allergens: 'Gluten, Dairy',
    popular: false,
  },
  {
    id: 5,
    name: 'Mango Juice',
    price: 4,
    category: 'Drinks',
    allergens: 'None',
    popular: false,
  },
  {
    id: 6,
    name: 'Garlic Bread',
    price: 5,
    category: 'Starters',
    allergens: 'Gluten',
    popular: false,
  },
  {
    id: 7,
    name: 'Beef Burger',
    price: 16,
    category: 'Mains',
    allergens: 'Gluten, Dairy',
    popular: true,
  },
  {
    id: 8,
    name: 'Tiramisu',
    price: 7,
    category: 'Desserts',
    allergens: 'Dairy, Eggs',
    popular: false,
  },
];
const TIME_SLOTS = [
  '12:00 PM',
  '1:00 PM',
  '2:00 PM',
  '6:00 PM',
  '7:00 PM',
  '8:00 PM',
  '9:00 PM',
];
const PAYMENT_METHODS = [
  {
    id: 'mpesa',
    label: 'M-Pesa',
    icon: 'phone-portrait-outline',
    color: '#4caf50',
    region: 'East Africa',
  },
  {
    id: 'card',
    label: 'Card',
    icon: 'card-outline',
    color: GOLD,
    region: 'Worldwide',
  },
  {
    id: 'paypal',
    label: 'PayPal',
    icon: 'logo-paypal',
    color: '#003087',
    region: 'International',
  },
  {
    id: 'apple',
    label: 'Apple Pay',
    icon: 'logo-apple',
    color: WHITE,
    region: 'International',
  },
  {
    id: 'google',
    label: 'Google Pay',
    icon: 'logo-google',
    color: '#4285F4',
    region: 'International',
  },
  {
    id: 'pesalink',
    label: 'PesaLink',
    icon: 'swap-horizontal-outline',
    color: '#e91e63',
    region: 'East Africa',
  },
  {
    id: 'airtel',
    label: 'Airtel Money',
    icon: 'wifi-outline',
    color: '#f44336',
    region: 'East Africa',
  },
  {
    id: 'bank',
    label: 'Bank Transfer',
    icon: 'business-outline',
    color: MUTED,
    region: 'Worldwide',
  },
];

function GuestApp({ setScreen, onSupport }) {
  const [guestView, setGuestView] = useState('home');
  const [guests, setGuests] = useState(2);
  const [selectedTime, setSelectedTime] = useState(null);
  const [selectedDate, setSelectedDate] = useState('Today');
  const [roomType, setRoomType] = useState(null);
  const [nights, setNights] = useState(1);
  const [menuCategory, setMenuCategory] = useState('All');
  const [bookingType, setBookingType] = useState('');
  const [cart, setCart] = useState({});
  const [payMethod, setPayMethod] = useState(null);
  const [cardNum, setCardNum] = useState('');
  const [cardName, setCardName] = useState('');
  const [cardExp, setCardExp] = useState('');
  const [cardCvv, setCardCvv] = useState('');
  const [paying, setPaying] = useState(false);
  const [orderTotal, setOrderTotal] = useState(0);
  const [supportOpen, setSupportOpen] = useState(false);
  const [guestName, setGuestName] = useState('');
  const [guestEmail, setGuestEmail] = useState('');
  const [specialReq, setSpecialReq] = useState('');

  const categories = ['All', 'Starters', 'Mains', 'Desserts', 'Drinks'];
  const filteredMenu =
    menuCategory === 'All'
      ? MENU_ITEMS
      : MENU_ITEMS.filter((m) => m.category === menuCategory);
  const cartTotal = MENU_ITEMS.filter((i) => cart[i.id] > 0).reduce(
    (s, i) => s + i.price * cart[i.id],
    0
  );
  const cartCount = Object.values(cart).reduce((a, b) => a + b, 0);

  const goToPayment = (type, total) => {
    setBookingType(type);
    setOrderTotal(total);
    setPayMethod(null);
    setCardNum('');
    setCardName('');
    setCardExp('');
    setCardCvv('');
    setGuestView('payment');
  };

  const handlePay = () => {
    if (!payMethod) {
      Alert.alert('Select a payment method.');
      return;
    }
    if (
      payMethod === 'card' &&
      (!cardNum.trim() ||
        !cardName.trim() ||
        !cardExp.trim() ||
        !cardCvv.trim())
    ) {
      Alert.alert('Fill in all card details.');
      return;
    }
    setPaying(true);
    logEvent('GUEST_PAYMENT', bookingType + ' — $' + orderTotal);
    setTimeout(() => {
      setPaying(false);
      setCart({});
      setGuestView('paid');
    }, 1800);
  };

  const GuestTopBar = ({ title, back }) => (
    <View style={styles.topBar}>
      <TouchableOpacity
        onPress={back || (() => setGuestView('home'))}
        style={styles.topBarBtn}>
        <Ionicons name="arrow-back" size={22} color={WHITE} />
      </TouchableOpacity>
      <Text style={styles.topBarTitle}>{title}</Text>
      <TouchableOpacity
        onPress={() => setSupportOpen(true)}
        style={styles.topBarBtn}>
        <Ionicons name="headset-outline" size={22} color={GOLD} />
      </TouchableOpacity>
    </View>
  );

  /* HOME */
  if (guestView === 'home')
    return (
      <ScrollView style={styles.page}>
        <SupportModal
          visible={supportOpen}
          onClose={() => setSupportOpen(false)}
          currentUser={null}
        />
        <View style={styles.topBar}>
          <TouchableOpacity
            onPress={() => setScreen('login')}
            style={styles.topBarBtn}>
            <Ionicons name="arrow-back" size={22} color={WHITE} />
          </TouchableOpacity>
          <Text style={styles.topBarTitle}>Guest Portal</Text>
          <TouchableOpacity
            onPress={() => setSupportOpen(true)}
            style={styles.topBarBtn}>
            <Ionicons name="headset-outline" size={22} color={GOLD} />
          </TouchableOpacity>
        </View>

        <View
          style={[
            styles.card,
            { marginTop: 6, borderLeftWidth: 3, borderLeftColor: GOLD },
          ]}>
          <Text
            style={{
              color: GOLD,
              fontSize: 16,
              fontWeight: 'bold',
              marginBottom: 4,
            }}>
            Welcome to NEXA
          </Text>
          <Text style={{ color: MUTED, fontSize: 12 }}>
            Your luxury experience starts here. No sign-in required.
          </Text>
        </View>

        {/* Cart badge */}
        {cartCount > 0 && (
          <TouchableOpacity
            onPress={() => setGuestView('menu')}
            style={[
              styles.card,
              {
                flexDirection: 'row',
                alignItems: 'center',
                borderWidth: 1,
                borderColor: GOLD,
              },
            ]}>
            <Ionicons name="cart-outline" size={22} color={GOLD} />
            <Text
              style={{
                color: WHITE,
                fontSize: 14,
                fontWeight: 'bold',
                marginLeft: 10,
              }}>
              Your Cart
            </Text>
            <View
              style={{
                backgroundColor: GOLD,
                borderRadius: 12,
                paddingHorizontal: 8,
                paddingVertical: 3,
                marginLeft: 'auto',
              }}>
              <Text
                style={{ color: '#1a1200', fontWeight: 'bold', fontSize: 12 }}>
                {cartCount} item(s) — ${cartTotal}
              </Text>
            </View>
          </TouchableOpacity>
        )}

        {[
          {
            label: 'Book a Table',
            icon: 'restaurant-outline',
            view: 'table',
            desc: 'Reserve your dining experience',
          },
          {
            label: 'Book a Room',
            icon: 'bed-outline',
            view: 'room',
            desc: 'Standard, Deluxe, Suite available',
          },
          {
            label: 'Browse Menu',
            icon: 'fast-food-outline',
            view: 'menu',
            desc: 'Order food and drinks',
          },
          {
            label: 'Concierge',
            icon: 'information-circle-outline',
            view: 'concierge',
            desc: 'Local tips and hotel services',
          },
        ].map((item) => (
          <TouchableOpacity
            key={item.view}
            style={[
              styles.card,
              { flexDirection: 'row', alignItems: 'center' },
            ]}
            onPress={() => setGuestView(item.view)}>
            <View
              style={{
                backgroundColor: GOLD + '22',
                borderRadius: 10,
                padding: 10,
                marginRight: 14,
              }}>
              <Ionicons name={item.icon} size={24} color={GOLD} />
            </View>
            <View style={{ flex: 1 }}>
              <Text style={{ color: WHITE, fontSize: 15, fontWeight: 'bold' }}>
                {item.label}
              </Text>
              <Text style={{ color: MUTED, fontSize: 11, marginTop: 2 }}>
                {item.desc}
              </Text>
            </View>
            <Ionicons name="chevron-forward-outline" size={18} color={MUTED} />
          </TouchableOpacity>
        ))}
      </ScrollView>
    );

  /* TABLE BOOKING */
  if (guestView === 'table')
    return (
      <ScrollView style={styles.page}>
        <SupportModal
          visible={supportOpen}
          onClose={() => setSupportOpen(false)}
          currentUser={null}
        />
        <GuestTopBar title="Book a Table" />
        <View style={styles.card}>
          <Text style={styles.cardTitle}>Your Details</Text>
          {[
            { placeholder: 'Full Name', value: guestName, set: setGuestName },
            { placeholder: 'Email', value: guestEmail, set: setGuestEmail },
            {
              placeholder: 'Special Requests (optional)',
              value: specialReq,
              set: setSpecialReq,
            },
          ].map((f, i) => (
            <View
              key={i}
              style={[styles.inputWrap, { width: '100%', marginBottom: 8 }]}>
              <TextInput
                placeholder={f.placeholder}
                placeholderTextColor={MUTED}
                style={styles.inputField}
                value={f.value}
                onChangeText={f.set}
              />
            </View>
          ))}
        </View>
        <View style={styles.card}>
          <Text style={styles.cardTitle}>Date</Text>
          <ScrollView horizontal showsHorizontalScrollIndicator={false}>
            {['Today', 'Tomorrow', 'Wed', 'Thu', 'Fri'].map((d) => (
              <TouchableOpacity
                key={d}
                onPress={() => setSelectedDate(d)}
                style={[
                  styles.chip,
                  selectedDate === d && styles.chipActive,
                  { marginBottom: 4 },
                ]}>
                <Text
                  style={[
                    styles.chipText,
                    selectedDate === d && { color: '#1a1200' },
                  ]}>
                  {d}
                </Text>
              </TouchableOpacity>
            ))}
          </ScrollView>
        </View>
        <View style={styles.card}>
          <Text style={styles.cardTitle}>Guests</Text>
          <View
            style={{
              flexDirection: 'row',
              alignItems: 'center',
              marginTop: 4,
            }}>
            <TouchableOpacity
              onPress={() => setGuests(Math.max(1, guests - 1))}
              style={styles.counterBtn}>
              <Text style={styles.counterBtnText}>-</Text>
            </TouchableOpacity>
            <Text
              style={{
                color: WHITE,
                fontSize: 22,
                fontWeight: 'bold',
                marginHorizontal: 20,
              }}>
              {guests}
            </Text>
            <TouchableOpacity
              onPress={() => setGuests(Math.min(20, guests + 1))}
              style={styles.counterBtn}>
              <Text style={styles.counterBtnText}>+</Text>
            </TouchableOpacity>
          </View>
        </View>
        <View style={styles.card}>
          <Text style={styles.cardTitle}>Time Slot</Text>
          <View
            style={{ flexDirection: 'row', flexWrap: 'wrap', marginTop: 4 }}>
            {TIME_SLOTS.map((t) => (
              <TouchableOpacity
                key={t}
                onPress={() => setSelectedTime(t)}
                style={[
                  styles.chip,
                  selectedTime === t && styles.chipActive,
                  { marginBottom: 8, marginRight: 8 },
                ]}>
                <Text
                  style={[
                    styles.chipText,
                    selectedTime === t && { color: '#1a1200' },
                  ]}>
                  {t}
                </Text>
              </TouchableOpacity>
            ))}
          </View>
        </View>
        <TouchableOpacity
          style={[styles.mainBtn, { width: '100%', marginTop: 16 }]}
          onPress={() => {
            if (!selectedTime) {
              Alert.alert('Select a time slot.');
              return;
            }
            goToPayment('Table', 20);
          }}>
          <Text style={styles.btnText}>Proceed to Payment — $20</Text>
        </TouchableOpacity>
      </ScrollView>
    );

  /* ROOM BOOKING */
  if (guestView === 'room')
    return (
      <ScrollView style={styles.page}>
        <SupportModal
          visible={supportOpen}
          onClose={() => setSupportOpen(false)}
          currentUser={null}
        />
        <GuestTopBar title="Book a Room" />
        <View style={styles.card}>
          <Text style={styles.cardTitle}>Room Type</Text>
          {[
            {
              type: 'Standard',
              price: 80,
              icon: 'bed-outline',
              desc: 'Cozy with garden view, WiFi, TV',
            },
            {
              type: 'Deluxe',
              price: 130,
              icon: 'star-outline',
              desc: 'City view, minibar, premium linen',
            },
            {
              type: 'Suite',
              price: 220,
              icon: 'diamond-outline',
              desc: 'Full luxury, private lounge, Jacuzzi',
            },
          ].map((r) => (
            <TouchableOpacity
              key={r.type}
              onPress={() => setRoomType(r.type)}
              style={[
                styles.bookingRow,
                { paddingVertical: 12 },
                roomType === r.type && {
                  backgroundColor: GOLD + '22',
                  borderRadius: 8,
                  paddingHorizontal: 8,
                },
              ]}>
              <Ionicons
                name={r.icon}
                size={20}
                color={GOLD}
                style={{ marginRight: 10 }}
              />
              <View style={{ flex: 1 }}>
                <Text style={{ color: WHITE, fontWeight: 'bold' }}>
                  {r.type}
                </Text>
                <Text style={{ color: MUTED, fontSize: 11 }}>{r.desc}</Text>
                <Text
                  style={{
                    color: GOLD,
                    fontWeight: 'bold',
                    fontSize: 12,
                    marginTop: 2,
                  }}>
                  ${r.price}/night
                </Text>
              </View>
              {roomType === r.type && (
                <Ionicons name="checkmark-circle" size={20} color={GOLD} />
              )}
            </TouchableOpacity>
          ))}
        </View>
        <View style={styles.card}>
          <Text style={styles.cardTitle}>Nights</Text>
          <View
            style={{
              flexDirection: 'row',
              alignItems: 'center',
              marginTop: 4,
            }}>
            <TouchableOpacity
              onPress={() => setNights(Math.max(1, nights - 1))}
              style={styles.counterBtn}>
              <Text style={styles.counterBtnText}>-</Text>
            </TouchableOpacity>
            <Text
              style={{
                color: WHITE,
                fontSize: 22,
                fontWeight: 'bold',
                marginHorizontal: 20,
              }}>
              {nights}
            </Text>
            <TouchableOpacity
              onPress={() => setNights(nights + 1)}
              style={styles.counterBtn}>
              <Text style={styles.counterBtnText}>+</Text>
            </TouchableOpacity>
          </View>
        </View>
        {roomType && (
          <View style={[styles.card, { borderWidth: 1, borderColor: GOLD }]}>
            <Text style={styles.cardTitle}>Summary</Text>
            <View
              style={{ flexDirection: 'row', justifyContent: 'space-between' }}>
              <Text style={{ color: MUTED }}>
                {roomType} × {nights} night(s)
              </Text>
              <Text style={{ color: GOLD, fontWeight: 'bold' }}>
                ${{ Standard: 80, Deluxe: 130, Suite: 220 }[roomType] * nights}
              </Text>
            </View>
          </View>
        )}
        <TouchableOpacity
          style={[styles.mainBtn, { width: '100%', marginTop: 16 }]}
          onPress={() => {
            if (!roomType) {
              Alert.alert('Select a room type.');
              return;
            }
            const prices = { Standard: 80, Deluxe: 130, Suite: 220 };
            goToPayment('Room', prices[roomType] * nights);
          }}>
          <Text style={styles.btnText}>Proceed to Payment</Text>
        </TouchableOpacity>
      </ScrollView>
    );

  /* MENU */
  if (guestView === 'menu')
    return (
      <ScrollView style={styles.page}>
        <SupportModal
          visible={supportOpen}
          onClose={() => setSupportOpen(false)}
          currentUser={null}
        />
        <GuestTopBar title="Our Menu" />
        <ScrollView
          horizontal
          showsHorizontalScrollIndicator={false}
          style={{ marginBottom: 10 }}>
          {categories.map((c) => (
            <TouchableOpacity
              key={c}
              onPress={() => setMenuCategory(c)}
              style={[styles.chip, menuCategory === c && styles.chipActive]}>
              <Text
                style={[
                  styles.chipText,
                  menuCategory === c && { color: '#1a1200' },
                ]}>
                {c}
              </Text>
            </TouchableOpacity>
          ))}
        </ScrollView>
        {filteredMenu.map((item) => {
          const qty = cart[item.id] || 0;
          return (
            <View
              key={item.id}
              style={[
                styles.card,
                { flexDirection: 'row', alignItems: 'center', marginTop: 8 },
              ]}>
              <View
                style={{
                  backgroundColor: GOLD + '22',
                  borderRadius: 8,
                  padding: 10,
                  marginRight: 12,
                }}>
                <Ionicons name="fast-food-outline" size={20} color={GOLD} />
              </View>
              <View style={{ flex: 1 }}>
                <View style={{ flexDirection: 'row', alignItems: 'center' }}>
                  <Text style={{ color: WHITE, fontWeight: 'bold' }}>
                    {item.name}
                  </Text>
                  {item.popular && (
                    <View
                      style={{
                        backgroundColor: GOLD + '33',
                        borderRadius: 8,
                        paddingHorizontal: 6,
                        paddingVertical: 2,
                        marginLeft: 6,
                      }}>
                      <Text style={{ color: GOLD, fontSize: 9 }}>Popular</Text>
                    </View>
                  )}
                </View>
                <Text style={{ color: MUTED, fontSize: 10 }}>
                  {item.category}
                </Text>
                {item.allergens !== 'None' && (
                  <Text style={{ color: AMBER, fontSize: 9, marginTop: 1 }}>
                    ⚠ {item.allergens}
                  </Text>
                )}
                <Text style={{ color: GOLD, fontWeight: 'bold', marginTop: 2 }}>
                  ${item.price}
                </Text>
              </View>
              <View style={{ flexDirection: 'row', alignItems: 'center' }}>
                <TouchableOpacity
                  onPress={() =>
                    setCart((prev) => ({
                      ...prev,
                      [item.id]: Math.max(0, (prev[item.id] || 0) - 1),
                    }))
                  }
                  style={[styles.counterBtn, { width: 28, height: 28 }]}>
                  <Text style={[styles.counterBtnText, { fontSize: 16 }]}>
                    -
                  </Text>
                </TouchableOpacity>
                <Text
                  style={{
                    color: WHITE,
                    fontWeight: 'bold',
                    marginHorizontal: 8,
                    minWidth: 16,
                    textAlign: 'center',
                  }}>
                  {qty}
                </Text>
                <TouchableOpacity
                  onPress={() =>
                    setCart((prev) => ({
                      ...prev,
                      [item.id]: (prev[item.id] || 0) + 1,
                    }))
                  }
                  style={[styles.counterBtn, { width: 28, height: 28 }]}>
                  <Text style={[styles.counterBtnText, { fontSize: 16 }]}>
                    +
                  </Text>
                </TouchableOpacity>
              </View>
            </View>
          );
        })}
        {cartCount > 0 && (
          <TouchableOpacity
            style={[
              styles.mainBtn,
              { width: '100%', marginTop: 16, marginBottom: 30 },
            ]}
            onPress={() => goToPayment('Order', cartTotal)}>
            <Ionicons
              name="cart-outline"
              size={18}
              color="#1a1200"
              style={{ marginRight: 8 }}
            />
            <Text style={styles.btnText}>Pay for Order — ${cartTotal}</Text>
          </TouchableOpacity>
        )}
      </ScrollView>
    );

  /* CONCIERGE */
  if (guestView === 'concierge')
    return (
      <ScrollView style={styles.page}>
        <SupportModal
          visible={supportOpen}
          onClose={() => setSupportOpen(false)}
          currentUser={null}
        />
        <GuestTopBar title="Concierge" />
        <View style={styles.card}>
          <Text style={styles.cardTitle}>Hotel Services</Text>
          {[
            {
              icon: 'car-outline',
              label: 'Airport Transfer',
              desc: 'Book a pickup or drop-off',
            },
            {
              icon: 'shirt-outline',
              label: 'Laundry Service',
              desc: 'Same day service available',
            },
            {
              icon: 'flower-outline',
              label: 'Room Service',
              desc: '24/7 in-room dining',
            },
            {
              icon: 'fitness-outline',
              label: 'Gym & Spa',
              desc: 'Open 6AM–10PM',
            },
            {
              icon: 'business-outline',
              label: 'Conference Rooms',
              desc: 'Bookable for meetings',
            },
            {
              icon: 'wifi-outline',
              label: 'WiFi',
              desc: 'Password: NEXA2024 (free)',
            },
          ].map((s) => (
            <View
              key={s.label}
              style={{
                flexDirection: 'row',
                alignItems: 'center',
                paddingVertical: 12,
                borderBottomWidth: 1,
                borderBottomColor: '#ffffff08',
              }}>
              <View
                style={{
                  backgroundColor: GOLD + '22',
                  borderRadius: 8,
                  padding: 8,
                  marginRight: 12,
                }}>
                <Ionicons name={s.icon} size={18} color={GOLD} />
              </View>
              <View>
                <Text
                  style={{ color: WHITE, fontWeight: 'bold', fontSize: 13 }}>
                  {s.label}
                </Text>
                <Text style={{ color: MUTED, fontSize: 11 }}>{s.desc}</Text>
              </View>
            </View>
          ))}
        </View>
        <View style={[styles.card, { marginBottom: 30 }]}>
          <Text style={styles.cardTitle}>Nearby Attractions</Text>
          {[
            { name: 'Nairobi National Park', dist: '8 km' },
            { name: 'Westgate Mall', dist: '2 km' },
            { name: 'Karen Blixen Museum', dist: '12 km' },
            { name: 'KICC', dist: '3 km' },
          ].map((a) => (
            <View
              key={a.name}
              style={{
                flexDirection: 'row',
                justifyContent: 'space-between',
                paddingVertical: 8,
                borderBottomWidth: 1,
                borderBottomColor: '#ffffff08',
              }}>
              <Text style={{ color: WHITE, fontSize: 13 }}>{a.name}</Text>
              <Text style={{ color: MUTED, fontSize: 12 }}>{a.dist}</Text>
            </View>
          ))}
        </View>
      </ScrollView>
    );

  /* PAYMENT */
  if (guestView === 'payment')
    return (
      <ScrollView style={styles.page}>
        <SupportModal
          visible={supportOpen}
          onClose={() => setSupportOpen(false)}
          currentUser={null}
        />
        <GuestTopBar
          title="Payment"
          back={() =>
            setGuestView(
              bookingType === 'Table'
                ? 'table'
                : bookingType === 'Room'
                ? 'room'
                : 'menu'
            )
          }
        />

        <View style={styles.card}>
          <Text style={styles.cardTitle}>Order Summary</Text>
          <View
            style={{
              flexDirection: 'row',
              justifyContent: 'space-between',
              marginBottom: 4,
            }}>
            <Text style={{ color: MUTED, fontSize: 13 }}>
              {bookingType === 'Table'
                ? 'Table Reservation'
                : bookingType === 'Room'
                ? roomType + ' Room ×' + nights + 'n'
                : 'Food Order'}
            </Text>
            <Text style={{ color: GOLD, fontWeight: 'bold', fontSize: 18 }}>
              ${orderTotal}
            </Text>
          </View>
          {bookingType === 'Table' && (
            <Text style={{ color: MUTED, fontSize: 11 }}>
              {selectedDate +
                ' • ' +
                selectedTime +
                ' • ' +
                guests +
                ' guest(s)'}
            </Text>
          )}
        </View>

        <View style={styles.card}>
          <Text style={styles.cardTitle}>Payment Method</Text>
          <Text style={{ color: MUTED, fontSize: 10, marginBottom: 12 }}>
            East Africa & International options supported
          </Text>
          <View style={{ flexDirection: 'row', flexWrap: 'wrap' }}>
            {PAYMENT_METHODS.map((pm) => (
              <TouchableOpacity
                key={pm.id}
                onPress={() => setPayMethod(pm.id)}
                style={{
                  width: '46%',
                  margin: '2%',
                  backgroundColor: payMethod === pm.id ? pm.color + '30' : BG,
                  borderWidth: payMethod === pm.id ? 2 : 1,
                  borderColor: payMethod === pm.id ? pm.color : '#ffffff12',
                  borderRadius: 12,
                  padding: 12,
                  alignItems: 'center',
                }}>
                <Ionicons name={pm.icon} size={24} color={pm.color} />
                <Text
                  style={{
                    color: WHITE,
                    fontSize: 12,
                    fontWeight: 'bold',
                    marginTop: 6,
                  }}>
                  {pm.label}
                </Text>
                <Text style={{ color: MUTED, fontSize: 9, marginTop: 2 }}>
                  {pm.region}
                </Text>
              </TouchableOpacity>
            ))}
          </View>
        </View>

        {(payMethod === 'mpesa' ||
          payMethod === 'pesalink' ||
          payMethod === 'airtel') && (
          <View style={styles.card}>
            <Text style={styles.cardTitle}>
              {payMethod === 'mpesa'
                ? 'M-Pesa'
                : payMethod === 'pesalink'
                ? 'PesaLink'
                : 'Airtel Money'}
            </Text>
            {payMethod === 'mpesa' && (
              <Text style={{ color: MUTED, fontSize: 12, marginBottom: 8 }}>
                An STK push will be sent to your phone.
              </Text>
            )}
            <View style={[styles.inputWrap, { width: '100%' }]}>
              <Ionicons
                name="phone-portrait-outline"
                size={18}
                color={GOLD}
                style={styles.inputIcon}
              />
              <TextInput
                placeholder="+254 7XX XXX XXX"
                placeholderTextColor={MUTED}
                style={styles.inputField}
                keyboardType="phone-pad"
                value={cardNum}
                onChangeText={setCardNum}
              />
            </View>
          </View>
        )}

        {payMethod === 'card' && (
          <View style={styles.card}>
            <Text style={styles.cardTitle}>Card Details</Text>
            <Text style={{ color: MUTED, fontSize: 10, marginBottom: 10 }}>
              Visa • Mastercard • Amex
            </Text>
            {[
              {
                placeholder: 'Card number',
                icon: 'card-outline',
                kbType: 'numeric',
                max: 19,
                secure: false,
                val: cardNum,
                set: setCardNum,
              },
              {
                placeholder: 'Cardholder name',
                icon: 'person-outline',
                kbType: 'default',
                max: 50,
                secure: false,
                val: cardName,
                set: setCardName,
              },
            ].map((f, i) => (
              <View
                key={i}
                style={[styles.inputWrap, { width: '100%', marginBottom: 8 }]}>
                <Ionicons
                  name={f.icon}
                  size={18}
                  color={GOLD}
                  style={styles.inputIcon}
                />
                <TextInput
                  placeholder={f.placeholder}
                  placeholderTextColor={MUTED}
                  style={styles.inputField}
                  keyboardType={f.kbType}
                  maxLength={f.max}
                  secureTextEntry={f.secure}
                  value={f.val}
                  onChangeText={f.set}
                />
              </View>
            ))}
            <View style={{ flexDirection: 'row' }}>
              <View style={[styles.inputWrap, { flex: 1, marginRight: 8 }]}>
                <Ionicons
                  name="calendar-outline"
                  size={18}
                  color={GOLD}
                  style={styles.inputIcon}
                />
                <TextInput
                  placeholder="MM/YY"
                  placeholderTextColor={MUTED}
                  style={styles.inputField}
                  maxLength={5}
                  keyboardType="numeric"
                  value={cardExp}
                  onChangeText={setCardExp}
                />
              </View>
              <View style={[styles.inputWrap, { flex: 1 }]}>
                <Ionicons
                  name="lock-closed-outline"
                  size={18}
                  color={GOLD}
                  style={styles.inputIcon}
                />
                <TextInput
                  placeholder="CVV"
                  placeholderTextColor={MUTED}
                  style={styles.inputField}
                  maxLength={4}
                  keyboardType="numeric"
                  secureTextEntry
                  value={cardCvv}
                  onChangeText={setCardCvv}
                />
              </View>
            </View>
          </View>
        )}

        {payMethod === 'bank' && (
          <View style={styles.card}>
            <Text style={styles.cardTitle}>Bank Transfer</Text>
            {[
              { label: 'Bank', value: 'Equity Bank Kenya' },
              { label: 'Account', value: '0123456789' },
              { label: 'Name', value: 'NEXA Hospitality Ltd' },
              { label: 'Ref', value: 'BK-' + Date.now().toString().slice(-6) },
            ].map((r) => (
              <View
                key={r.label}
                style={{
                  flexDirection: 'row',
                  justifyContent: 'space-between',
                  paddingVertical: 6,
                  borderBottomWidth: 1,
                  borderBottomColor: '#ffffff08',
                }}>
                <Text style={{ color: MUTED, fontSize: 12 }}>{r.label}</Text>
                <Text
                  style={{ color: WHITE, fontSize: 12, fontWeight: 'bold' }}>
                  {r.value}
                </Text>
              </View>
            ))}
          </View>
        )}

        {(payMethod === 'paypal' ||
          payMethod === 'apple' ||
          payMethod === 'google') && (
          <View style={styles.card}>
            <Text style={styles.cardTitle}>
              {payMethod === 'paypal'
                ? 'PayPal'
                : payMethod === 'apple'
                ? 'Apple Pay'
                : 'Google Pay'}
            </Text>
            <Text
              style={{
                color: MUTED,
                fontSize: 13,
                textAlign: 'center',
                marginVertical: 10,
              }}>
              {'You will be redirected to complete your $' +
                orderTotal +
                ' payment securely.'}
            </Text>
          </View>
        )}

        <View
          style={{
            flexDirection: 'row',
            alignItems: 'center',
            justifyContent: 'center',
            marginTop: 12,
            marginBottom: 6,
          }}>
          <Ionicons name="shield-checkmark-outline" size={13} color={MUTED} />
          <Text style={{ color: MUTED, fontSize: 11, marginLeft: 5 }}>
            256-bit SSL • PCI DSS Compliant
          </Text>
        </View>

        <TouchableOpacity
          style={[
            styles.mainBtn,
            { width: '100%', marginTop: 8, marginBottom: 30 },
          ]}
          onPress={handlePay}
          disabled={paying}>
          {paying ? (
            <ActivityIndicator color="#1a1200" />
          ) : (
            <View style={{ flexDirection: 'row', alignItems: 'center' }}>
              <Ionicons
                name="lock-closed-outline"
                size={16}
                color="#1a1200"
                style={{ marginRight: 6 }}
              />
              <Text style={styles.btnText}>
                {'Pay $' + orderTotal + ' Securely'}
              </Text>
            </View>
          )}
        </TouchableOpacity>
      </ScrollView>
    );

  /* PAID */
  if (guestView === 'paid')
    return (
      <ScrollView
        contentContainerStyle={[
          styles.page,
          { alignItems: 'center', paddingTop: 60 },
        ]}>
        <HotelBg />
        <View
          style={{
            backgroundColor: GREEN + '18',
            borderRadius: 60,
            padding: 24,
            marginBottom: 20,
            borderWidth: 2,
            borderColor: GREEN + '40',
          }}>
          <Ionicons name="checkmark-circle" size={64} color={GREEN} />
        </View>
        <Text style={[styles.logo, { fontSize: 22, textAlign: 'center' }]}>
          Payment Successful!
        </Text>
        <Text style={{ color: MUTED, textAlign: 'center', marginTop: 8 }}>
          {bookingType === 'Table'
            ? selectedDate +
              ' at ' +
              selectedTime +
              ' for ' +
              guests +
              ' guest(s)'
            : bookingType === 'Room'
            ? roomType + ' Room for ' + nights + ' night(s)'
            : 'Your food order'}
        </Text>
        <Text
          style={{
            color: GOLD,
            fontWeight: 'bold',
            fontSize: 22,
            marginVertical: 12,
          }}>
          ${orderTotal} paid
        </Text>
        <Text style={{ color: MUTED, fontSize: 11, marginBottom: 8 }}>
          Ref: CNF-{Date.now().toString().slice(-6)}
        </Text>
        <View
          style={{
            flexDirection: 'row',
            alignItems: 'center',
            marginBottom: 30,
          }}>
          <Ionicons name="mail-outline" size={14} color={MUTED} />
          <Text style={{ color: MUTED, fontSize: 12, marginLeft: 6 }}>
            Receipt sent to your email.
          </Text>
        </View>
        <TouchableOpacity
          style={[styles.mainBtn, { width: '100%' }]}
          onPress={() => {
            setGuestView('home');
            setPayMethod(null);
          }}>
          <Text style={styles.btnText}>Back to Home</Text>
        </TouchableOpacity>
      </ScrollView>
    );

  return null;
}

/* ─── STYLES ──────────────────────────────────────────────────────────────────── */
const styles = StyleSheet.create({
  app: { flex: 1, backgroundColor: BG },
  center: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: BG,
  },

  logoWrap: { alignItems: 'center', marginBottom: 24 },
  logo: { fontSize: 38, color: GOLD, fontWeight: 'bold', letterSpacing: 6 },
  subtitle: { color: MUTED, fontSize: 11, letterSpacing: 3, marginTop: 2 },
  logoDivider: {
    width: 60,
    height: 1,
    backgroundColor: GOLD,
    marginTop: 12,
    opacity: 0.5,
  },

  topBar: {
    flexDirection: 'row',
    alignItems: 'center',
    justifyContent: 'space-between',
    paddingVertical: 10,
    paddingHorizontal: 4,
    marginBottom: 4,
  },
  topBarTitle: {
    color: WHITE,
    fontWeight: 'bold',
    fontSize: 16,
    flex: 1,
    textAlign: 'center',
  },
  topBarBtn: { padding: 8, position: 'relative' },

  inputWrap: {
    flexDirection: 'row',
    alignItems: 'center',
    backgroundColor: CARD,
    borderRadius: 10,
    marginBottom: 6,
    borderWidth: 1,
    borderColor: '#ffffff10',
    width: 300,
  },
  inputIcon: { paddingLeft: 12 },
  inputField: { flex: 1, padding: 12, color: WHITE },
  errorText: {
    color: DANGER,
    fontSize: 11,
    alignSelf: 'flex-start',
    marginBottom: 4,
    marginLeft: 4,
  },

  mainBtn: {
    backgroundColor: GOLD,
    padding: 13,
    borderRadius: 10,
    alignItems: 'center',
    marginTop: 8,
    flexDirection: 'row',
    justifyContent: 'center',
  },
  btnText: { fontWeight: 'bold', color: '#1a1200', fontSize: 14 },
  socialBtn: {
    flexDirection: 'row',
    alignItems: 'center',
    padding: 9,
    borderRadius: 8,
    margin: 5,
  },
  socialText: { color: WHITE, marginLeft: 5, fontSize: 12 },

  page: { flex: 1, padding: 16, backgroundColor: BG },
  statsRow: { flexDirection: 'row', justifyContent: 'space-between' },
  statCard: {
    backgroundColor: CARD,
    padding: 12,
    borderRadius: 12,
    width: '30%',
    borderWidth: 1,
    borderColor: '#ffffff08',
    alignItems: 'center',
  },
  statValue: { color: GOLD, fontSize: 18, fontWeight: 'bold' },
  statTitle: { color: MUTED, fontSize: 9, marginTop: 2, textAlign: 'center' },
  card: {
    backgroundColor: CARD,
    padding: 15,
    borderRadius: 12,
    marginTop: 12,
    borderWidth: 1,
    borderColor: '#ffffff08',
  },
  cardTitle: {
    color: WHITE,
    marginBottom: 10,
    fontWeight: 'bold',
    fontSize: 14,
  },
  cardHeader: {
    flexDirection: 'row',
    justifyContent: 'space-between',
    alignItems: 'center',
    marginBottom: 4,
  },

  chip: {
    borderWidth: 1,
    borderColor: GOLD,
    borderRadius: 20,
    paddingHorizontal: 14,
    paddingVertical: 5,
    marginRight: 8,
  },
  chipActive: { backgroundColor: GOLD },
  chipText: { color: GOLD, fontSize: 12 },

  bookingRow: {
    flexDirection: 'row',
    alignItems: 'center',
    paddingVertical: 8,
    borderBottomWidth: 1,
    borderBottomColor: '#ffffff08',
  },
  statusPill: {
    paddingHorizontal: 8,
    paddingVertical: 3,
    borderRadius: 12,
    fontSize: 11,
    fontWeight: 'bold',
  },
  rowText: { color: WHITE },

  badge: {
    position: 'absolute',
    top: -4,
    right: -4,
    backgroundColor: DANGER,
    borderRadius: 8,
    width: 16,
    height: 16,
    justifyContent: 'center',
    alignItems: 'center',
  },
  badgeText: { color: WHITE, fontSize: 10, fontWeight: 'bold' },

  addBtn: {
    flexDirection: 'row',
    alignItems: 'center',
    backgroundColor: GOLD,
    paddingHorizontal: 10,
    paddingVertical: 5,
    borderRadius: 8,
  },
  formBox: {
    backgroundColor: BG,
    borderRadius: 10,
    padding: 12,
    marginBottom: 10,
    borderWidth: 1,
    borderColor: '#ffffff08',
  },

  orderBtnText: { fontSize: 12, fontWeight: 'bold' },
  orderBtnGreen: {
    flexDirection: 'row',
    alignItems: 'center',
    borderWidth: 1,
    borderColor: GREEN,
    backgroundColor: GREEN + '18',
    borderRadius: 8,
    paddingHorizontal: 10,
    paddingVertical: 6,
  },
  orderBtnAmber: {
    flexDirection: 'row',
    alignItems: 'center',
    borderWidth: 1,
    borderColor: AMBER,
    backgroundColor: AMBER + '18',
    borderRadius: 8,
    paddingHorizontal: 10,
    paddingVertical: 6,
  },
  orderBtnBlue: {
    flexDirection: 'row',
    alignItems: 'center',
    borderWidth: 1,
    borderColor: ACCENT,
    backgroundColor: ACCENT + '18',
    borderRadius: 8,
    paddingHorizontal: 10,
    paddingVertical: 6,
  },
  orderBtnRed: {
    flexDirection: 'row',
    alignItems: 'center',
    borderWidth: 1,
    borderColor: DANGER,
    backgroundColor: DANGER + '18',
    borderRadius: 8,
    paddingHorizontal: 10,
    paddingVertical: 6,
  },

  counterBtn: {
    backgroundColor: GOLD,
    borderRadius: 8,
    width: 34,
    height: 34,
    justifyContent: 'center',
    alignItems: 'center',
  },
  counterBtnText: { fontSize: 20, fontWeight: 'bold', color: '#1a1200' },
});
