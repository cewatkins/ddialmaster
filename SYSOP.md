# Diversi-DIAL System Operator Guide

## Initial System Setup

### First Boot Configuration
1. **Boot from cassette** (4-minute load time)
2. **Configure modems** using Option #9 from main menu
3. **Set system time** using `/CT` command
4. **Create MASTER account** (first user automatically gets MASTER status)
5. **Configure system parameters** using `/CF` command

### Essential First Steps
```
1. /CT                    # Set correct time/date
2. /A sysop masterpass    # Create main sysop account
3. /CF                    # Configure system settings
4. /CM                    # Configure each modem slot
5. /CN                    # Configure network settings (if linking)
```

## Daily Operations

### Morning Startup Routine
1. **Check system status** - Review overnight activity
2. **Read system logs** - `/LG` to see any issues
3. **Monitor call statistics** - Check 24-hour totals
4. **Verify modem status** - Ensure all lines operational
5. **Check disk space** - Monitor storage usage

### Daily Maintenance Tasks
```
/STATS              # Review system statistics
/LG                 # Check system logs
/L                  # Review user accounts
/USAGE              # Check system usage patterns
/AUDIT              # Security audit (weekly)
```

### End of Day Procedures
1. **Save system logs** - `/LS` to preserve daily activity
2. **Backup user database** - `/BACKUP` for data protection
3. **Review peak usage** - `/PEAK` for capacity planning
4. **Check overnight schedule** - Verify system ready for unattended operation

## User Account Management

### Creating User Accounts
```
# Standard User
/A username password     # Basic user account

# PASSWORD User (Moderator)
/A modname modpass       # Create account
/M modname               # Modify to PASSWORD status

# MASTER User (Co-SysOp)
/A cosysop masterpass    # Create account
/M cosysop               # Modify to MASTER status
```

### Account Security Levels
- **Standard Users**: Chat, email, basic commands
- **PASSWORD Users**: User management, logs, system config
- **MASTER Users**: Full system control, debug access

### User Account Maintenance
```
/L                      # List all accounts with status
/M username             # Modify account settings
/D username             # Delete inactive accounts
/BAN username           # Ban problematic users
/UNBAN username         # Remove user bans
```

## System Monitoring

### Real-Time Monitoring
- **Top Display Lines**: Always show system status
- **Line 1**: Cutoff time, line assignments, time limits, caller times
- **Line 2**: Channel status, call counts, date/time

### Status Indicators
- **Line Numbers (1234567)**: Show active connections
- **Channel Display (1-4)**: Chat channel activity (* = offline)
- **Time Limits**: Minutes remaining for non-PASSWORD users
- **Lock Indicator**: Inverse "-" when non-PASSWORD users locked out
- **Login Status**: "!" during signon, "+/*" for PASSWORD type

### Monitoring Commands
```
/MONITOR 3              # Watch line 3 activity
/W                      # Who's currently online
/CL                     # Active chat channels
/STATS                  # Detailed system statistics
```

## Log Management

### System Logs
- **Login/Logout Events**: Track user sessions
- **Command Usage**: Monitor system usage patterns
- **Error Messages**: Identify system problems
- **Security Events**: Track suspicious activity

### Log Commands
```
/LG                     # Display recent log entries
/LC                     # Clear logs (after saving)
/LS                     # Save logs to disk
/LP                     # Print logs (if printer available)
```

### Log Analysis
1. **Daily Review**: Check for unusual activity
2. **Weekly Analysis**: Identify usage trends
3. **Monthly Reports**: Generate operational statistics
4. **Security Audits**: Review access patterns

## System Configuration

### Basic System Settings
```
/CF                     # Main configuration menu
  - System name
  - Welcome message
  - Time limits
  - User cutoffs
  - Security settings
```

### Modem Configuration
```
/CM                     # Modem configuration
  - Slot assignments (1-7)
  - Baud rates
  - Initialization strings
  - Answer behavior
```

### Network Configuration
```
/CN                     # Network linking setup
  - Station identification
  - Link protocols
  - Routing tables
  - Synchronization
```

## Troubleshooting Common Issues

### Connection Problems
**Symptom**: Users can't connect to specific lines
**Solution**:
1. Check modem configuration (`/CM`)
2. Verify phone line status
3. Test modem initialization
4. Check slot assignments

### Performance Issues
**Symptom**: System running slowly
**Solution**:
1. Check memory usage (`/STATS`)
2. Review active user count
3. Monitor disk activity
4. Consider user limits

### Login Problems
**Symptom**: Users can't login
**Solution**:
1. Verify user account exists (`/L`)
2. Check account status
3. Review security settings
4. Check time limits

### Email Issues
**Symptom**: Email not working
**Solution**:
1. Verify 80-column card installed
2. Check memory configuration
3. Test email commands
4. Review user permissions

## Security Management

### Access Control
- **User Levels**: Standard, PASSWORD, MASTER
- **Time Limits**: Automatic cutoffs for non-PASSWORD users
- **Login Restrictions**: Lock out non-PASSWORD users when needed
- **Account Monitoring**: Track user activity patterns

### Security Commands
```
/LOCKOUT                # Lock out non-PASSWORD users
/BAN username           # Ban specific user
/TRACE username         # Monitor user activity
/AUDIT                  # Generate security report
```

### Security Best Practices
1. **Regular Password Changes**: Especially for MASTER accounts
2. **Account Reviews**: Monthly audit of user accounts
3. **Activity Monitoring**: Watch for unusual patterns
4. **Backup Security**: Protect backup media
5. **Physical Security**: Secure computer and phone lines

## Network Operations (Multi-Station)

### Station Linking Setup
1. **Hardware Installation**: Interface Two parallel cards
2. **Cable Connection**: Link computers via parallel ports
3. **Software Configuration**: Configure station IDs
4. **Test Links**: Verify communication between stations

### Network Commands
```
/LINK                   # Manage station links
/CONNECT station2       # Establish link to station2
/STATUS station2        # Check station2 status
/SYNC station2          # Synchronize user databases
/SEND station2 message  # Send message to station2
```

### Network Maintenance
- **Daily Link Tests**: Verify all connections
- **Database Sync**: Keep user databases synchronized
- **Load Balancing**: Distribute users across stations
- **Backup Coordination**: Ensure all stations backed up

## Backup and Recovery

### Backup Procedures
```
/BACKUP                 # System backup utility
  - User database
  - System configuration
  - Email messages
  - System logs
```

### Backup Schedule
- **Daily**: User database and logs
- **Weekly**: Full system backup
- **Monthly**: Archive old backups
- **Before Changes**: Backup before major modifications

### Recovery Procedures
```
/RESTORE                # System restore utility
  - Select backup date
  - Choose restore components
  - Verify data integrity
  - Test system function
```

## Performance Optimization

### System Tuning
```
/OPTIMIZE               # System optimization
  - Memory management
  - Disk optimization
  - Network tuning
  - User limits
```

### Capacity Planning
- **Monitor Peak Usage**: Track busy periods
- **User Growth**: Plan for expanding user base
- **Hardware Limits**: Understand system constraints
- **Upgrade Planning**: Prepare for hardware upgrades

### Performance Monitoring
1. **Response Times**: Monitor system responsiveness
2. **Throughput**: Track message and email volume
3. **Concurrent Users**: Monitor simultaneous connections
4. **Resource Usage**: Memory and disk utilization

## Emergency Procedures

### System Recovery
**Complete System Failure**:
1. Power cycle the Apple //e
2. Reload from cassette (4 minutes)
3. Restore from last backup
4. Verify system operation
5. Check all modem connections

### Partial System Failure
**Individual Line Problems**:
1. Check modem configuration
2. Test phone line
3. Restart specific modem
4. Check cable connections

### Network Link Failure
**Station Communication Loss**:
1. Check parallel card connections
2. Verify cable integrity
3. Test individual stations
4. Restart network services

## Advanced Administration

### System Debugging
```
/DEBUG                  # Enter debug mode
/TRACE                  # Enable system tracing
/DUMP                   # Memory dump utilities
/CHECK                  # System integrity check
```

### Custom Configuration
- **Modify System Messages**: Customize user experience
- **Adjust Time Limits**: Optimize for user patterns
- **Configure Auto-Features**: Set up automated functions
- **Create Custom Commands**: Add site-specific features

### Integration with Other Systems
- **PC Pursuit**: Long-distance networking
- **Local BBSs**: Message exchange
- **Bulletin Systems**: News distribution
- **File Transfer**: Document sharing

## Operational Best Practices

### System Administration
1. **Document Changes**: Keep detailed change logs
2. **Test Procedures**: Test all changes in isolation
3. **User Communication**: Inform users of maintenance
4. **Regular Reviews**: Monthly operational assessments

### User Management
1. **Clear Policies**: Establish and communicate rules
2. **Fair Enforcement**: Apply policies consistently
3. **User Feedback**: Listen to user suggestions
4. **Community Building**: Foster positive environment

### Technical Operations
1. **Preventive Maintenance**: Regular system checks
2. **Spare Hardware**: Keep backup modems and cards
3. **Documentation**: Maintain system documentation
4. **Training**: Cross-train multiple operators

This comprehensive guide provides the foundation for successful Diversi-DIAL system operation and administration.